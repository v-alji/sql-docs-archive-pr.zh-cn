---
title: 多个优先约束 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- multiple precedence constraints
- precedence executables [Integration Services]
- precedence constraints [Integration Services], multiple
- constrained executables [Integration Services]
ms.assetid: 71c53ead-3d19-4bc1-aafd-e5b32595b420
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 16fefbbf886818989131710876564fc9e147a56a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586795"
---
# <a name="multiple-precedence-constraints"></a><span data-ttu-id="d93cc-102">多个优先约束</span><span class="sxs-lookup"><span data-stu-id="d93cc-102">Multiple Precedence Constraints</span></span>
  <span data-ttu-id="d93cc-103">一个优先约束连接两个可执行文件：两个任务、两个容器或一个任务和一个容器。</span><span class="sxs-lookup"><span data-stu-id="d93cc-103">A precedence constraint connects two executables: two tasks, two containers, or one of each.</span></span> <span data-ttu-id="d93cc-104">它们被称为优先可执行文件和受约束的可执行文件。</span><span class="sxs-lookup"><span data-stu-id="d93cc-104">They are known as the precedence executable and the constrained executable.</span></span> <span data-ttu-id="d93cc-105">受约束的可执行文件可具有多个优先约束。</span><span class="sxs-lookup"><span data-stu-id="d93cc-105">A constrained executable can have multiple precedence constraints.</span></span> <span data-ttu-id="d93cc-106">有关详细信息，请参阅 [优先约束](control-flow/precedence-constraints.md)。</span><span class="sxs-lookup"><span data-stu-id="d93cc-106">For more information, see [Precedence Constraints](control-flow/precedence-constraints.md).</span></span>  
  
 <span data-ttu-id="d93cc-107">对约束进行分组以组合成复杂的约束方案，可使您在包中实现复杂的控制流。</span><span class="sxs-lookup"><span data-stu-id="d93cc-107">Assembling complex constraint scenarios by grouping constraints enables you to implement complex control flow in packages.</span></span> <span data-ttu-id="d93cc-108">例如，在下图中，一个 `Success` 约束将任务 D 链接到任务 A，一个 `Failure` 约束将任务 D 链接到任务 B，而一个 `Success` 约束将任务 D 链接到任务 C。</span><span class="sxs-lookup"><span data-stu-id="d93cc-108">For example, in the following illustration, Task D is linked to Task A by a `Success` constraint, Task D is linked to Task B by a `Failure` constraint, and Task D is linked to Task C by a `Success` constraint.</span></span> <span data-ttu-id="d93cc-109">任务 D 和任务 A 之间、任务 D 和任务 B 之间，以及任务 D 和任务 C 之间的优先约束参与逻辑与 \*\* 关系。</span><span class="sxs-lookup"><span data-stu-id="d93cc-109">The precedence constraints between Task D and Task A, between Task D and Task B, and between Task D and Task C participate in a logical *and* relationship.</span></span> <span data-ttu-id="d93cc-110">因此，任务 A 必须运行成功，任务 B 必须失败，并且任务 C 必须运行成功才能运行任务 D。</span><span class="sxs-lookup"><span data-stu-id="d93cc-110">Therefore, for Task D to run, Task A must run successfully, Task B must fail, and Task C must run successfully.</span></span>  
  
 <span data-ttu-id="d93cc-111">![按优先约束链接的任务](media/precedenceconstraints.gif "按优先约束链接的任务")</span><span class="sxs-lookup"><span data-stu-id="d93cc-111">![Tasks linked by precedence constraints](media/precedenceconstraints.gif "Tasks linked by precedence constraints")</span></span>  
  
## <a name="logicaland-property"></a><span data-ttu-id="d93cc-112">LogicalAnd 属性</span><span class="sxs-lookup"><span data-stu-id="d93cc-112">LogicalAnd Property</span></span>  
 <span data-ttu-id="d93cc-113">如果任务或容器具有多个约束，则 `LogicalAnd` 属性指定一个优先约束是单独计算还是与其他约束一起计算。</span><span class="sxs-lookup"><span data-stu-id="d93cc-113">If a task or a container has multiple constraints, the `LogicalAnd` property specifies whether a precedence constraint is evaluated singly or in concert with other constraints.</span></span>  
  
 <span data-ttu-id="d93cc-114">您可以 `LogicalAnd` 使用设计器中的 "**优先约束编辑器**" [!INCLUDE[ssIS](../includes/ssis-md.md)] ，或在提供的属性窗口中设置属性 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d93cc-114">You can set the `LogicalAnd` property using the **Precedence Constraint Editor** in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, or in the Properties window that [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] provides.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="d93cc-115">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="d93cc-115">Related Tasks</span></span>  
 [<span data-ttu-id="d93cc-116">设置优先约束的属性</span><span class="sxs-lookup"><span data-stu-id="d93cc-116">Set the Properties of a Precedence Constraint</span></span>](../../2014/integration-services/set-the-properties-of-a-precedence-constraint.md)  
  
  
