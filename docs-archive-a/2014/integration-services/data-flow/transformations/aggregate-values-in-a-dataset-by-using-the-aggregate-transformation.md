---
title: 使用聚合转换来聚合数据集中的值 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Aggregate transformation [Integration Services]
- aggregate values [Integration Services]
- datasets [Integration Services], aggregate values
ms.assetid: 01b81c0f-d5e0-483b-81b2-73800a6945ac
author: chugugrace
ms.author: chugu
ms.openlocfilehash: de918c6c2adf194d5808ccd1b64c77a94a52e357
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682972"
---
# <a name="aggregate-values-in-a-dataset-by-using-the-aggregate-transformation"></a><span data-ttu-id="76def-102">使用聚合转换来聚合数据集中的值</span><span class="sxs-lookup"><span data-stu-id="76def-102">Aggregate Values in a Dataset by Using the Aggregate Transformation</span></span>
  <span data-ttu-id="76def-103">若要添加并配置聚合转换，则包必须已包含至少一个数据流任务和一个源。</span><span class="sxs-lookup"><span data-stu-id="76def-103">To add and configure an Aggregate transformation, the package must already include at least one Data Flow task and one source.</span></span>  
  
### <a name="to-aggregate-values-in-a-dataset"></a><span data-ttu-id="76def-104">聚合数据集中的值</span><span class="sxs-lookup"><span data-stu-id="76def-104">To aggregate values in a dataset</span></span>  
  
1.  <span data-ttu-id="76def-105">在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="76def-105">In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="76def-106">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="76def-106">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="76def-107">单击 **“数据流”** 选项卡，然后从 **“工具箱”** 中将聚合转换拖动到设计图面。</span><span class="sxs-lookup"><span data-stu-id="76def-107">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the Aggregate transformation to the design surface.</span></span>  
  
4.  <span data-ttu-id="76def-108">将连接线从源或前一转换拖到聚合转换，从而将聚合转换连接到数据流。</span><span class="sxs-lookup"><span data-stu-id="76def-108">Connect the Aggregate transformation to the data flow by dragging a connector from the source or the previous transformation to the Aggregate transformation.</span></span>  
  
5.  <span data-ttu-id="76def-109">双击此转换。</span><span class="sxs-lookup"><span data-stu-id="76def-109">Double-click the transformation.</span></span>  
  
6.  <span data-ttu-id="76def-110">在 **“聚合转换编辑器”** 对话框中单击 **“聚合”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="76def-110">In the **Aggregate Transformation Editor** dialog box, click the **Aggregations** tab.</span></span>  
  
7.  <span data-ttu-id="76def-111">在 **“可用输入列”** 列表中，选中要对其值进行聚合运算的列旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="76def-111">In the **Available Input Columns** list, select the check box by the columns on which you want to aggregate values.</span></span> <span data-ttu-id="76def-112">所选的列出现在表中。</span><span class="sxs-lookup"><span data-stu-id="76def-112">The selected columns appear in the table.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="76def-113">可以多次选择同一列，这样便可对此列应用多次转换。</span><span class="sxs-lookup"><span data-stu-id="76def-113">You can select a column multiple times, applying multiple transformations to the column.</span></span> <span data-ttu-id="76def-114">若要唯一标识聚合，请在列输出别名的默认名称后面追加一个数字。</span><span class="sxs-lookup"><span data-stu-id="76def-114">To uniquely identify aggregations, a number is appended to the default name of the output alias of the column.</span></span>  
  
8.  <span data-ttu-id="76def-115">或者，修改 **“输出别名”** 列中的值。</span><span class="sxs-lookup"><span data-stu-id="76def-115">Optionally, modify the value in the **Output Alias** columns.</span></span>  
  
9. <span data-ttu-id="76def-116">若要更改默认聚合操作 **“分组依据”** ，请选择 **“操作”** 列表中的其他操作。</span><span class="sxs-lookup"><span data-stu-id="76def-116">To change the default aggregation operation, **Group by**, select a different operation in the **Operation** list.</span></span>  
  
10. <span data-ttu-id="76def-117">若要更改默认比较，请选择 **“比较标志”** 列中所列出的单个比较标志。</span><span class="sxs-lookup"><span data-stu-id="76def-117">To change the default comparison, select the individual comparison flags listed in the **Comparison Flags** column.</span></span> <span data-ttu-id="76def-118">默认情况下，比较将忽略大小写、假名类型、不占位字符和字符宽度。</span><span class="sxs-lookup"><span data-stu-id="76def-118">By default, a comparison ignores case, kana type, non-spacing characters, and character width.</span></span>  
  
11. <span data-ttu-id="76def-119">对于 **“非重复计数”** 聚合，如果需要，可在 **“非重复键计数”** 列中指定非重复值的精确计数，或者在 **“非重复键数范围”** 列中选择近似的数字。</span><span class="sxs-lookup"><span data-stu-id="76def-119">Optionally, for the **Count distinct** aggregation, specify an exact number of distinct values in the **Count Distinct Keys** column, or select an approximate count in the **Count Distinct Scale** column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="76def-120">由于转换可以为它的工作预先分配合适的内存数量，因此可通过提供不同值的个数（准确或近似）来优化性能。</span><span class="sxs-lookup"><span data-stu-id="76def-120">Providing the number of distinct values, exact or approximate, optimizes performance, because the transformation can preallocate an appropriate amount of memory to do its work.</span></span>  
  
12. <span data-ttu-id="76def-121">或者，单击 **“高级”** 并更新聚合转换输出的名称。</span><span class="sxs-lookup"><span data-stu-id="76def-121">Optionally, click **Advanced** and update the name of the Aggregate transformation output.</span></span> <span data-ttu-id="76def-122">如果聚合包含 `Group By` 操作，则可以在 "**键范围**" 列中选择分组键值的近似计数，或者在 "**键**" 列中指定精确的分组键值。</span><span class="sxs-lookup"><span data-stu-id="76def-122">If the aggregations include a `Group By` operation, you can select an approximate count of grouping key values in the **Keys Scale** column or specify an exact number of grouping key values in the **Keys** column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="76def-123">由于转换可以为它的工作预先分配合适的内存数量，因此可通过提供不同值的个数（准确或近似）来优化性能。</span><span class="sxs-lookup"><span data-stu-id="76def-123">Providing the number of distinct values, exact or approximate, optimizes performance, because the transformation can preallocate an appropriate amount of memory to do its work.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="76def-124">**“键范围”** 和 **“键”** 选项互斥。</span><span class="sxs-lookup"><span data-stu-id="76def-124">The **Keys Scale** and **Keys** options are mutually exclusive.</span></span> <span data-ttu-id="76def-125">如果在两个列中都输入值，将使用 **“键范围”** 或 **“键”** 二者中的更大值。</span><span class="sxs-lookup"><span data-stu-id="76def-125">If you enter values in both columns, the larger value in either **Keys Scale** or **Keys** is used.</span></span>  
  
13. <span data-ttu-id="76def-126">或者，单击 **“高级”** 选项卡并设置应用于优化聚合转换所执行的所有操作的属性。</span><span class="sxs-lookup"><span data-stu-id="76def-126">Optionally, click the **Advanced** tab and set the attributes that apply to optimizing all the operations that the Aggregate transformation performs.</span></span>  
  
14. <span data-ttu-id="76def-127">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="76def-127">Click **OK**.</span></span>  
  
15. <span data-ttu-id="76def-128">若要保存更新后的包，请单击 **“文件”** 菜单上的 **“保存选定项”** 。</span><span class="sxs-lookup"><span data-stu-id="76def-128">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76def-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="76def-129">See Also</span></span>  
 <span data-ttu-id="76def-130">[聚合转换](aggregate-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="76def-130">[Aggregate Transformation](aggregate-transformation.md) </span></span>  
 <span data-ttu-id="76def-131">[Integration Services 转换](integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="76def-131">[Integration Services Transformations](integration-services-transformations.md) </span></span>  
 <span data-ttu-id="76def-132">[Integration Services 路径](../integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="76def-132">[Integration Services Paths](../integration-services-paths.md) </span></span>  
 [<span data-ttu-id="76def-133">数据流任务</span><span class="sxs-lookup"><span data-stu-id="76def-133">Data Flow Task</span></span>](../../control-flow/data-flow-task.md)  
  
  
