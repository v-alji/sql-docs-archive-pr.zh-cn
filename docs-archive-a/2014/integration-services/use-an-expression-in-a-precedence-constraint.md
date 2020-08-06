---
title: 在优先约束中使用表达式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- precedence constraints [Integration Services], adding expressions
- expressions [Integration Services], adding
ms.assetid: 601038bb-3b17-42ac-b09d-5b3a82fb6564
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a997efa448a8381cc8251cd4cbf69dc59f8968e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689940"
---
# <a name="use-an-expression-in-a-precedence-constraint"></a><span data-ttu-id="a0245-102">在优先约束中使用表达式</span><span class="sxs-lookup"><span data-stu-id="a0245-102">Use an Expression in a Precedence Constraint</span></span>
  <span data-ttu-id="a0245-103">此过程介绍如何使用 **“优先约束编辑器”** 对话框将表达式添加到优先约束中。</span><span class="sxs-lookup"><span data-stu-id="a0245-103">This procedure describes how to add an expression to a precedence constraint by using the **Precedence Constraint Editor** dialog box.</span></span> <span data-ttu-id="a0245-104">包中必须包含至少两个可执行文件（可以是任务或容器），并且它们必须由优先约束连接起来，才能将表达式添加到优先约束。</span><span class="sxs-lookup"><span data-stu-id="a0245-104">Before you can add an expression to a precedence constraint, the package must include at least two executables, either tasks or containers, and they must be connected by a precedence constraint.</span></span>  
  
### <a name="to-add-an-expression-to-a-precedence-constraint"></a><span data-ttu-id="a0245-105">将表达式添加到优先约束</span><span class="sxs-lookup"><span data-stu-id="a0245-105">To add an expression to a precedence constraint</span></span>  
  
1.  <span data-ttu-id="a0245-106">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="a0245-106">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="a0245-107">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="a0245-107">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="a0245-108">单击 **“控制流”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="a0245-108">Click the **Control Flow** tab.</span></span>  
  
4.  <span data-ttu-id="a0245-109">在“控制流”选项卡的设计图面上双击优先约束。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="a0245-109">On the design surface of the **Control Flow** tab, double-click the precedence constraint.</span></span> <span data-ttu-id="a0245-110">**“优先约束编辑器”** 将打开。</span><span class="sxs-lookup"><span data-stu-id="a0245-110">The **Precedence Constraint Editor** opens.</span></span>  
  
5.  <span data-ttu-id="a0245-111">在 **“求值运算”** 列表中选择 **“表达式”**、 **“表达式和约束”** 或者 **“表达式或约束”** 。</span><span class="sxs-lookup"><span data-stu-id="a0245-111">Select **Expression**, **Expression and Constraint**, or **Expression or Constraint** in the **Evaluation operation** list.</span></span>  
  
6.  <span data-ttu-id="a0245-112">在 **“表达式”** 文本框中键入表达式，或启动表达式生成器来创建表达式。</span><span class="sxs-lookup"><span data-stu-id="a0245-112">Type an expression in the **Expression** text box or launch the Expression Builder to create an expression.</span></span>  
  
7.  <span data-ttu-id="a0245-113">若要验证表达式语法，请单击 **“测试”**。</span><span class="sxs-lookup"><span data-stu-id="a0245-113">To validate the expression syntax, click **Test**.</span></span>  
  
8.  <span data-ttu-id="a0245-114">若要保存更新后的包，请单击 **“文件”** 菜单上的 **“保存选定项”** 。</span><span class="sxs-lookup"><span data-stu-id="a0245-114">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0245-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a0245-115">See Also</span></span>  
 <span data-ttu-id="a0245-116">[优先约束](control-flow/precedence-constraints.md) </span><span class="sxs-lookup"><span data-stu-id="a0245-116">[Precedence Constraints](control-flow/precedence-constraints.md) </span></span>  
 <span data-ttu-id="a0245-117">[使用默认优先约束来连接任务和容器](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md) </span><span class="sxs-lookup"><span data-stu-id="a0245-117">[Connect Tasks and Containers by Using a Default Precedence Constraint](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md) </span></span>  
 <span data-ttu-id="a0245-118">[使用快捷菜单设置优先约束的值](../../2014/integration-services/set-the-value-of-a-precedence-constraint-by-using-the-shortcut-menu.md) </span><span class="sxs-lookup"><span data-stu-id="a0245-118">[Set the Value of a Precedence Constraint by Using the Shortcut Menu](../../2014/integration-services/set-the-value-of-a-precedence-constraint-by-using-the-shortcut-menu.md) </span></span>  
 <span data-ttu-id="a0245-119">[设置优先约束的属性](../../2014/integration-services/set-the-properties-of-a-precedence-constraint.md) </span><span class="sxs-lookup"><span data-stu-id="a0245-119">[Set the Properties of a Precedence Constraint](../../2014/integration-services/set-the-properties-of-a-precedence-constraint.md) </span></span>  
 [<span data-ttu-id="a0245-120">Integration Services (SSIS) 表达式</span><span class="sxs-lookup"><span data-stu-id="a0245-120">Integration Services &#40;SSIS&#41; Expressions</span></span>](expressions/integration-services-ssis-expressions.md)  
  
  
