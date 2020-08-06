---
title: For 循环编辑器 |Microsoft Docs
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.forloopcontainer.f1
ms.assetid: c4db9df6-d2f4-44da-9f4d-628893e86956
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b610805808e0f392e675ad79f16d2d39886c7f70
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578330"
---
# <a name="for-loop-editor"></a><span data-ttu-id="e870d-102">For 循环编辑器</span><span class="sxs-lookup"><span data-stu-id="e870d-102">For Loop Editor</span></span>
  <span data-ttu-id="e870d-103">可以使用 **“For 循环编辑器”** 对话框的 **“For 循环”** 页，配置只有在指定条件的计算结果为 False 时才会停止重复执行工作流的循环。</span><span class="sxs-lookup"><span data-stu-id="e870d-103">Use the **For Loop** page of the **For Loop Editor** dialog box to configure a loop that repeats a workflow until a specified condition evaluates to false.</span></span>  
  
 <span data-ttu-id="e870d-104">若要了解有关 For 循环容器以及如何在包中使用它的信息，请参阅 [For Loop Container](control-flow/for-loop-container.md)。</span><span class="sxs-lookup"><span data-stu-id="e870d-104">To learn about the For Loop container and how to use it in packages, see [For Loop Container](control-flow/for-loop-container.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="e870d-105">选项</span><span class="sxs-lookup"><span data-stu-id="e870d-105">Options</span></span>  
 <span data-ttu-id="e870d-106">**InitExpression**</span><span class="sxs-lookup"><span data-stu-id="e870d-106">**InitExpression**</span></span>  
 <span data-ttu-id="e870d-107">提供初始化该循环所用值的表达式（可选）。</span><span class="sxs-lookup"><span data-stu-id="e870d-107">Optionally, provide an expression that initializes values used by the loop.</span></span>  
  
 <span data-ttu-id="e870d-108">**EvalExpression**</span><span class="sxs-lookup"><span data-stu-id="e870d-108">**EvalExpression**</span></span>  
 <span data-ttu-id="e870d-109">提供用于计算循环应停止还是继续的表达式。</span><span class="sxs-lookup"><span data-stu-id="e870d-109">Provide an expression to evaluate whether the loop should stop or continue.</span></span>  
  
 <span data-ttu-id="e870d-110">**AssignExpression**</span><span class="sxs-lookup"><span data-stu-id="e870d-110">**AssignExpression**</span></span>  
 <span data-ttu-id="e870d-111">提供在每次循环重复时更改条件的表达式（可选）。</span><span class="sxs-lookup"><span data-stu-id="e870d-111">Optionally, provide an expression that changes a condition each time that the loop repeats.</span></span>  
  
 <span data-ttu-id="e870d-112">**名称**</span><span class="sxs-lookup"><span data-stu-id="e870d-112">**Name**</span></span>  
 <span data-ttu-id="e870d-113">为 For 循环容器提供唯一的名称。</span><span class="sxs-lookup"><span data-stu-id="e870d-113">Provide a unique name for the For Loop container.</span></span> <span data-ttu-id="e870d-114">此名称用作任务图标中的标签。</span><span class="sxs-lookup"><span data-stu-id="e870d-114">This name is used as the label in the task icon.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e870d-115">对象名称在一个包内必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="e870d-115">Object names must be unique within a package.</span></span>  
  
 <span data-ttu-id="e870d-116">**说明**</span><span class="sxs-lookup"><span data-stu-id="e870d-116">**Description**</span></span>  
 <span data-ttu-id="e870d-117">提供 For 循环容器的说明。</span><span class="sxs-lookup"><span data-stu-id="e870d-117">Provide a description of the For Loop container.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e870d-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e870d-118">See Also</span></span>  
 <span data-ttu-id="e870d-119">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="e870d-119">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="e870d-120">[“表达式”页](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="e870d-120">[Expressions Page](expressions/expressions-page.md) </span></span>  
 <span data-ttu-id="e870d-121">[Foreach 循环容器](control-flow/foreach-loop-container.md) </span><span class="sxs-lookup"><span data-stu-id="e870d-121">[Foreach Loop Container](control-flow/foreach-loop-container.md) </span></span>  
 [<span data-ttu-id="e870d-122">配置 For 循环容器</span><span class="sxs-lookup"><span data-stu-id="e870d-122">Configure a For Loop Container</span></span>](../../2014/integration-services/configure-a-for-loop-container.md)  
  
  
