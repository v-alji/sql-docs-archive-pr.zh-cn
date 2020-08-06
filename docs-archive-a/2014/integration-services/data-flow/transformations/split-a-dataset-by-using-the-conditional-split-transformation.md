---
title: 使用有条件拆分转换拆分数据集 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Conditional Split transformation
- splitting dataset
- datasets [Integration Services], splitting
ms.assetid: 23b3e84f-9296-4dc9-81c0-c7f06ae3f1ff
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2efbc3973db1ab1b6b61f6de879e451319b50e49
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589788"
---
# <a name="split-a-dataset-by-using-the-conditional-split-transformation"></a><span data-ttu-id="fc0dd-102">使用有条件拆分转换拆分数据集</span><span class="sxs-lookup"><span data-stu-id="fc0dd-102">Split a Dataset by Using the Conditional Split Transformation</span></span>
  <span data-ttu-id="fc0dd-103">若要添加和配置有条件拆分转换，包必须已包含至少一个数据流任务和一个源。</span><span class="sxs-lookup"><span data-stu-id="fc0dd-103">To add and configure a Conditional Split transformation, the package must already include at least one Data Flow task and a source.</span></span>  
  
### <a name="to-conditionally-split-a-dataset"></a><span data-ttu-id="fc0dd-104">有条件地拆分数据集</span><span class="sxs-lookup"><span data-stu-id="fc0dd-104">To conditionally split a dataset</span></span>  
  
1.  <span data-ttu-id="fc0dd-105">在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="fc0dd-105">In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="fc0dd-106">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="fc0dd-106">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="fc0dd-107">单击 **“数据流”** 选项卡，并将有条件拆分转换从 **“工具箱”** 拖动到设计图面。</span><span class="sxs-lookup"><span data-stu-id="fc0dd-107">Click the **Data Flow** tab, and, from the **Toolbox**, drag the Conditional Split transformation to the design surface.</span></span>  
  
4.  <span data-ttu-id="fc0dd-108">将连接器从数据源或前一个转换拖到有条件拆分转换，从而将有条件拆分转换连接到数据流。</span><span class="sxs-lookup"><span data-stu-id="fc0dd-108">Connect the Conditional Split transformation to the data flow by dragging the connector from the data source or the previous transformation to the Conditional Split transformation.</span></span>  
  
5.  <span data-ttu-id="fc0dd-109">双击有条件拆分转换。</span><span class="sxs-lookup"><span data-stu-id="fc0dd-109">Double-click the Conditional Split transformation.</span></span>  
  
6.  <span data-ttu-id="fc0dd-110">在 **“有条件拆分转换编辑器”** 中，将变量、列、函数和运算符拖动到网格中的 **“条件”** 列，从而生成用作条件的表达式。</span><span class="sxs-lookup"><span data-stu-id="fc0dd-110">In the **Conditional Split Transformation Editor**, build the expressions to use as conditions by dragging variables, columns, functions, and operators to the **Condition** column in the grid.</span></span> <span data-ttu-id="fc0dd-111">或者，也可以在 **“条件”** 列中键入表达式。</span><span class="sxs-lookup"><span data-stu-id="fc0dd-111">Or, you can type the expression in the **Condition** column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fc0dd-112">变量或列可在多个表达式中使用。</span><span class="sxs-lookup"><span data-stu-id="fc0dd-112">A variable or column can be used in multiple expressions.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fc0dd-113">如果表达式无效，表达式文本将突出显示，列上的工具提示将对错误进行说明。</span><span class="sxs-lookup"><span data-stu-id="fc0dd-113">If the expression is not valid, the expression text is highlighted and a ToolTip on the column describes the errors.</span></span>  
  
7.  <span data-ttu-id="fc0dd-114">还可以在 **“输出名称”** 列中修改值。</span><span class="sxs-lookup"><span data-stu-id="fc0dd-114">Optionally, modify the values in the **Output Name** column.</span></span> <span data-ttu-id="fc0dd-115">默认名称为 Case 1、Case 2，依此类推。</span><span class="sxs-lookup"><span data-stu-id="fc0dd-115">The default names are Case 1, Case 2, and so forth.</span></span>  
  
8.  <span data-ttu-id="fc0dd-116">若要修改计算条件的顺序，请单击向上箭头或向下箭头。</span><span class="sxs-lookup"><span data-stu-id="fc0dd-116">To modify the sequence in which the conditions are evaluated, click the up arrow or down arrow.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fc0dd-117">将最可能遇到的条件放置在列表顶部。</span><span class="sxs-lookup"><span data-stu-id="fc0dd-117">Place the conditions that are most likely to be encountered at the top of the list.</span></span>  
  
9. <span data-ttu-id="fc0dd-118">对于不能匹配任何条件的数据行，如果需要，可以修改默认输出的名称。</span><span class="sxs-lookup"><span data-stu-id="fc0dd-118">Optionally, modify the name of the default output for data rows that do not match any condition.</span></span>  
  
10. <span data-ttu-id="fc0dd-119">若要配置错误输出，请单击 **“配置错误输出”** 。</span><span class="sxs-lookup"><span data-stu-id="fc0dd-119">To configure an error output, click **Configure Error Output**.</span></span> <span data-ttu-id="fc0dd-120">有关详细信息，请参阅 [在数据流组件中配置错误输出](../../configure-an-error-output-in-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="fc0dd-120">For more information, see [Configure an Error Output in a Data Flow Component](../../configure-an-error-output-in-a-data-flow-component.md).</span></span>  
  
11. <span data-ttu-id="fc0dd-121">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="fc0dd-121">Click **OK**.</span></span>  
  
12. <span data-ttu-id="fc0dd-122">若要保存更新后的包，请单击 **“文件”** 菜单上的 **“保存选定项”** 。</span><span class="sxs-lookup"><span data-stu-id="fc0dd-122">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc0dd-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fc0dd-123">See Also</span></span>  
 <span data-ttu-id="fc0dd-124">[Conditional Split Transformation](conditional-split-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="fc0dd-124">[Conditional Split Transformation](conditional-split-transformation.md) </span></span>  
 <span data-ttu-id="fc0dd-125">[Integration Services 转换](integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="fc0dd-125">[Integration Services Transformations](integration-services-transformations.md) </span></span>  
 <span data-ttu-id="fc0dd-126">[Integration Services 路径](../integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="fc0dd-126">[Integration Services Paths](../integration-services-paths.md) </span></span>  
 <span data-ttu-id="fc0dd-127">[Integration Services 数据类型](../integration-services-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="fc0dd-127">[Integration Services Data Types](../integration-services-data-types.md) </span></span>  
 <span data-ttu-id="fc0dd-128">[数据流任务](../../control-flow/data-flow-task.md) </span><span class="sxs-lookup"><span data-stu-id="fc0dd-128">[Data Flow Task](../../control-flow/data-flow-task.md) </span></span>  
 [<span data-ttu-id="fc0dd-129">Integration Services (SSIS) 表达式</span><span class="sxs-lookup"><span data-stu-id="fc0dd-129">Integration Services &#40;SSIS&#41; Expressions</span></span>](../../expressions/integration-services-ssis-expressions.md)  
  
  
