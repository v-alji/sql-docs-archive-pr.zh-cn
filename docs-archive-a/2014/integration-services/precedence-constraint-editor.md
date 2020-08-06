---
title: 优先约束编辑器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.precedenceconstraint.f1
helpviewer_keywords:
- Precedence Constraint Editor dialog box
ms.assetid: b10d4330-6e35-4037-b309-ef56efcd60c5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b6853d1974f4276361d60e1d73b34c72a366a7f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579619"
---
# <a name="precedence-constraint-editor"></a><span data-ttu-id="bf095-102">优先约束编辑器</span><span class="sxs-lookup"><span data-stu-id="bf095-102">Precedence Constraint Editor</span></span>
  <span data-ttu-id="bf095-103">可以使用 **“优先约束编辑器”** 对话框配置优先约束。</span><span class="sxs-lookup"><span data-stu-id="bf095-103">Use the **Precedence Constraint Editor** dialog box to configure precedence constraints.</span></span>  
  
## <a name="options"></a><span data-ttu-id="bf095-104">选项</span><span class="sxs-lookup"><span data-stu-id="bf095-104">Options</span></span>  
 <span data-ttu-id="bf095-105">**求值运算**</span><span class="sxs-lookup"><span data-stu-id="bf095-105">**Evaluation operation**</span></span>  
 <span data-ttu-id="bf095-106">指定优先约束使用的求值运算。</span><span class="sxs-lookup"><span data-stu-id="bf095-106">Specify the evaluation operation that the precedence constraint uses.</span></span> <span data-ttu-id="bf095-107">运算包括：“约束”、“表达式”、“表达式和约束”和“表达式或约束”。</span><span class="sxs-lookup"><span data-stu-id="bf095-107">The operations are: **Constraint**, **Expression**, **Expression and Constraint**, and **Expression or Constraint**.</span></span>  
  
 <span data-ttu-id="bf095-108">**值**</span><span class="sxs-lookup"><span data-stu-id="bf095-108">**Value**</span></span>  
 <span data-ttu-id="bf095-109">指定约束值：“成功”、“失败”或“完成”。</span><span class="sxs-lookup"><span data-stu-id="bf095-109">Specify the constraint value: **Success**, **Failure**, or **Completion**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bf095-110"> 优先约束线的含义：绿色表示 **“成功”**，突出显示表示 **“失败”**，蓝色表示 **“完成”**。</span><span class="sxs-lookup"><span data-stu-id="bf095-110">The precedence constraint line is green for **Success**, highlighted for **Failure**, and blue for **Completion**.</span></span>  
  
 <span data-ttu-id="bf095-111">**表达式**</span><span class="sxs-lookup"><span data-stu-id="bf095-111">**Expression**</span></span>  
 <span data-ttu-id="bf095-112">如果使用运算“表达式”\*\*\*\*、“表达式和约束”\*\*\*\* 或“表达式或约束”\*\*\*\*，则键入一个表达式或启动表达式生成器来创建表达式。</span><span class="sxs-lookup"><span data-stu-id="bf095-112">If using the operations **Expression**, **Expression and Constraint**, or **Expression or Constraint**, type an expression or launch the Expression Builder to create the expression.</span></span> <span data-ttu-id="bf095-113">表达式的计算结果必须为布尔值。</span><span class="sxs-lookup"><span data-stu-id="bf095-113">The expression must evaluate to a Boolean.</span></span>  
  
 <span data-ttu-id="bf095-114">**Test**</span><span class="sxs-lookup"><span data-stu-id="bf095-114">**Test**</span></span>  
 <span data-ttu-id="bf095-115">验证表达式。</span><span class="sxs-lookup"><span data-stu-id="bf095-115">Validate the expression.</span></span>  
  
 <span data-ttu-id="bf095-116">**逻辑与**</span><span class="sxs-lookup"><span data-stu-id="bf095-116">**Logical AND**</span></span>  
 <span data-ttu-id="bf095-117">选择此选项可以指定：同一个可执行文件的多个优先约束必须一起计算。</span><span class="sxs-lookup"><span data-stu-id="bf095-117">Select to specify that multiple precedence constraints on the same executable must be evaluated together.</span></span> <span data-ttu-id="bf095-118">所有约束的计算结果都必须为 `True`。</span><span class="sxs-lookup"><span data-stu-id="bf095-118">All constraints must evaluate to `True`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bf095-119">这种类型的优先约束显示为绿色、突出显示或蓝色实线。</span><span class="sxs-lookup"><span data-stu-id="bf095-119">This type of precedence constraint appears as a solid green, highlighted or blue line.</span></span>  
  
 <span data-ttu-id="bf095-120">**逻辑或**</span><span class="sxs-lookup"><span data-stu-id="bf095-120">**Logical OR**</span></span>  
 <span data-ttu-id="bf095-121">选择此选项可以指定：同一个可执行文件的多个优先约束必须一起计算。</span><span class="sxs-lookup"><span data-stu-id="bf095-121">Select to specify that multiple precedence constraints on the same executable must be evaluated together.</span></span> <span data-ttu-id="bf095-122">至少必须有一个约束的计算结果为 `True`。</span><span class="sxs-lookup"><span data-stu-id="bf095-122">At least one constraint must evaluate to `True`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bf095-123">这种类型的优先约束显示为绿色、突出显示或蓝色点线。</span><span class="sxs-lookup"><span data-stu-id="bf095-123">This type of precedence constraint appears as a dotted green, highlighted, or blue line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf095-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bf095-124">See Also</span></span>  
 <span data-ttu-id="bf095-125">[优先约束](control-flow/precedence-constraints.md) </span><span class="sxs-lookup"><span data-stu-id="bf095-125">[Precedence Constraints](control-flow/precedence-constraints.md) </span></span>  
 <span data-ttu-id="bf095-126">[Integration Services 任务](control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="bf095-126">[Integration Services Tasks](control-flow/integration-services-tasks.md) </span></span>  
 <span data-ttu-id="bf095-127">[Integration Services 容器](control-flow/integration-services-containers.md) </span><span class="sxs-lookup"><span data-stu-id="bf095-127">[Integration Services Containers](control-flow/integration-services-containers.md) </span></span>  
 [<span data-ttu-id="bf095-128">Integration Services (SSIS) 表达式</span><span class="sxs-lookup"><span data-stu-id="bf095-128">Integration Services &#40;SSIS&#41; Expressions</span></span>](expressions/integration-services-ssis-expressions.md)  
  
  
