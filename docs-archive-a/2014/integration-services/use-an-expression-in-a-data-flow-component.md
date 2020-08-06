---
title: 在数据流组件中使用表达式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- components [Integration Services], data flow
- expressions [Integration Services], data flow components
ms.assetid: 9181b998-d24a-41fb-bb3c-14eee34f910d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 653bf468d0af6d44c5abe7344fcc13f93f86b430
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690704"
---
# <a name="use-an-expression-in-a-data-flow-component"></a><span data-ttu-id="3906a-102">在数据流组件中使用表达式</span><span class="sxs-lookup"><span data-stu-id="3906a-102">Use an Expression in a Data Flow Component</span></span>
  <span data-ttu-id="3906a-103">本过程介绍如何将表达式添加到有条件拆分转换或派生列转换中。</span><span class="sxs-lookup"><span data-stu-id="3906a-103">This procedure describes how to add an expression to the Conditional Split transformation or to the Derived Column transformation.</span></span> <span data-ttu-id="3906a-104">有条件拆分转换使用表达式定义将数据行定向到转换输出的条件，而派生列转换使用表达式定义分配给列的值。</span><span class="sxs-lookup"><span data-stu-id="3906a-104">The Conditional Split transformation uses expressions to define the conditions that direct data rows to a transformation output, and the Derived Column transformation uses expressions to define values assigned to columns.</span></span>  
  
 <span data-ttu-id="3906a-105">若要在转换中实现表达式，包必须至少已经包含一项数据流任务和一个源。</span><span class="sxs-lookup"><span data-stu-id="3906a-105">To implement an expression in a transformation, the package must already include at least one Data Flow task and a source.</span></span> <span data-ttu-id="3906a-106">有关将项添加到包中的信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="3906a-106">For information about adding items to packages, see the following topics:</span></span>  
  
-   [<span data-ttu-id="3906a-107">在控制流中添加或删除任务或容器</span><span class="sxs-lookup"><span data-stu-id="3906a-107">Add or Delete a Task or a Container in a Control Flow</span></span>](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
    
  
-   [<span data-ttu-id="3906a-108">在数据流中添加或删除组件</span><span class="sxs-lookup"><span data-stu-id="3906a-108">Add or Delete a Component in a Data Flow</span></span>](data-flow/add-or-delete-a-component-in-a-data-flow.md)  
  
-   [<span data-ttu-id="3906a-109">连接数据流中的组件</span><span class="sxs-lookup"><span data-stu-id="3906a-109">Connect Components in a Data Flow</span></span>](data-flow/connect-components-in-a-data-flow.md)  
  
### <a name="to-create-an-expression"></a><span data-ttu-id="3906a-110">创建表达式</span><span class="sxs-lookup"><span data-stu-id="3906a-110">To create an expression</span></span>  
  
1.  <span data-ttu-id="3906a-111">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="3906a-111">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="3906a-112">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="3906a-112">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="3906a-113">在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器中，单击 **“控制流”** 选项卡，然后单击包含要在其中实现表达式的数据流的数据流任务。</span><span class="sxs-lookup"><span data-stu-id="3906a-113">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click the **Control Flow** tab, and then click the Data Flow task that contains the data flow in which you want to implement an expression.</span></span>  
  
4.  <span data-ttu-id="3906a-114">单击 **“数据流”** 选项卡，然后将有条件拆分转换或派生列转换从 **“工具箱”** 拖到设计图面。</span><span class="sxs-lookup"><span data-stu-id="3906a-114">Click the **Data Flow** tab, and drag either a Conditional Split or Derived Column transformation from the **Toolbox** to the design surface.</span></span>  
  
5.  <span data-ttu-id="3906a-115">将绿色的连接器从源或转换拖到有条件拆分转换或派生列转换。</span><span class="sxs-lookup"><span data-stu-id="3906a-115">Drag the green connector from the source or a transformation to the Conditional Split or Derived Column transformation.</span></span>  
  
6.  <span data-ttu-id="3906a-116">双击该转换打开其对话框。</span><span class="sxs-lookup"><span data-stu-id="3906a-116">Double-click the transformation to open its dialog box.</span></span>  
  
7.  <span data-ttu-id="3906a-117">在左窗格中，展开“变量”显示系统变量和用户定义的变量，然后展开“列”显示转换输入列。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="3906a-117">In the left pane, expand **Variables** to display system and user-defined variables, and expand **Columns** to display the transformation input columns.</span></span>  
  
8.  <span data-ttu-id="3906a-118">在右窗格中，展开“数学函数”、“字符串函数”、“日期/时间函数”、“NULL 函数”、“类型转换”和“运算符”，访问表达式语法提供的函数、转换和运算符。\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="3906a-118">In the right pane, expand **Mathematical Functions**, **String Functions**, **Date/Time Functions**, **NULL Functions**, **Type Casts**, and **Operators** to access the functions, the casts, and the operators that the expression grammar provides.</span></span>  
  
9. <span data-ttu-id="3906a-119">根据转换的类型，可以执行下列某项操作来生成表达式：</span><span class="sxs-lookup"><span data-stu-id="3906a-119">Depending on the transformation, do one of the following to build an expression:</span></span>  
  
    -   <span data-ttu-id="3906a-120">在 **“有条件拆分转换编辑器”** 对话框中，将变量、列、函数、运算符和转换拖到 **“条件”** 列中。</span><span class="sxs-lookup"><span data-stu-id="3906a-120">In the **Conditional Split Transformation Editor** dialog box, drag variables, columns, functions, operators, and casts to the **Condition** column.</span></span> <span data-ttu-id="3906a-121">另外，您还可以直接在 **“条件”** 列中键入表达式。</span><span class="sxs-lookup"><span data-stu-id="3906a-121">Alternatively, you can type an expression directly in the **Condition** column.</span></span>  
  
    -   <span data-ttu-id="3906a-122">在 **“派生列转换编辑器”** 对话框中，将变量、列、函数、运算符和转换拖到 **“表达式”** 列中。</span><span class="sxs-lookup"><span data-stu-id="3906a-122">In the **Derived Column Transformation Editor** dialog box, drag variables, columns, functions, operators, and casts to the **Expression** column.</span></span> <span data-ttu-id="3906a-123">另外，您还可以直接在 **“表达式”** 列中键入表达式。</span><span class="sxs-lookup"><span data-stu-id="3906a-123">Alternatively, you can type an expression directly in the **Expression** column.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="3906a-124"> 当焦点离开 **“条件”** 列或 **“表达式”** 列时，表达式文本可能会突出显示，指示表达式语法不正确。</span><span class="sxs-lookup"><span data-stu-id="3906a-124">When you remove the focus from the **Condition** column or the **Expression** column, the expression text might be highlighted to indicate that the expression syntax is incorrect.</span></span>  
  
10. <span data-ttu-id="3906a-125">单击 **“确定”**，退出对话框。</span><span class="sxs-lookup"><span data-stu-id="3906a-125">Click **OK** to exit the dialog box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3906a-126">如果该表达式无效，则会出现一个警告，描述表达式中的语法错误。</span><span class="sxs-lookup"><span data-stu-id="3906a-126">If the expression is not valid, an alert appears describing the syntax errors in the expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3906a-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3906a-127">See Also</span></span>  
 <span data-ttu-id="3906a-128">[Integration Services &#40;SSIS&#41; 表达式](expressions/integration-services-ssis-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="3906a-128">[Integration Services &#40;SSIS&#41; Expressions](expressions/integration-services-ssis-expressions.md) </span></span>  
 <span data-ttu-id="3906a-129">[有条件拆分转换](data-flow/transformations/conditional-split-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="3906a-129">[Conditional Split Transformation](data-flow/transformations/conditional-split-transformation.md) </span></span>  
 <span data-ttu-id="3906a-130">[Derived Column Transformation](data-flow/transformations/derived-column-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="3906a-130">[Derived Column Transformation](data-flow/transformations/derived-column-transformation.md) </span></span>  
 <span data-ttu-id="3906a-131">[数据流任务](control-flow/data-flow-task.md) </span><span class="sxs-lookup"><span data-stu-id="3906a-131">[Data Flow Task](control-flow/data-flow-task.md) </span></span>  
 [<span data-ttu-id="3906a-132">数据流</span><span class="sxs-lookup"><span data-stu-id="3906a-132">Data Flow</span></span>](data-flow/data-flow.md)  
  
  
