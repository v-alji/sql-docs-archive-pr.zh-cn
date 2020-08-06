---
title: Web 服务任务编辑器 (输入页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.webservicestask.input.f1
helpviewer_keywords:
- Web Service Task Editor
ms.assetid: 93529c88-f540-47f2-a10a-12c87318ed6f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0ae876572747b9bb1088fe8b0a1c2c2fdde9f4f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590265"
---
# <a name="web-service-task-editor-input-page"></a><span data-ttu-id="291a1-102">Web 服务任务编辑器（“输入”页）</span><span class="sxs-lookup"><span data-stu-id="291a1-102">Web Service Task Editor (Input Page)</span></span>
  <span data-ttu-id="291a1-103">可以使用 **“Web 服务任务编辑器”** 对话框的 **“输入”** 页，指定 Web 服务、Web 方法和作为输入提供给 Web 方法的值。</span><span class="sxs-lookup"><span data-stu-id="291a1-103">Use the **Input** page of the **Web Service Task Editor** dialog box to specify the Web Service, the Web method, and the values to provide to the Web method as input.</span></span> <span data-ttu-id="291a1-104">可通过直接在“值”列中键入字符串或在“值”列中选择变量来提供这些值。</span><span class="sxs-lookup"><span data-stu-id="291a1-104">The values can be provided either by typing strings directly in the Value column, or by selecting variables in the Value column.</span></span>  
  
 <span data-ttu-id="291a1-105">若要了解此任务，请参阅 [Web 服务任务](control-flow/web-service-task.md)。</span><span class="sxs-lookup"><span data-stu-id="291a1-105">To learn about this task, see [Web Service Task](control-flow/web-service-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="291a1-106">选项</span><span class="sxs-lookup"><span data-stu-id="291a1-106">Options</span></span>  
 <span data-ttu-id="291a1-107">**服务**</span><span class="sxs-lookup"><span data-stu-id="291a1-107">**Service**</span></span>  
 <span data-ttu-id="291a1-108">从列表中选择用来执行 Web 方法的 Web 服务。</span><span class="sxs-lookup"><span data-stu-id="291a1-108">Select a Web service from the list to use to execute the Web method.</span></span>  
  
 <span data-ttu-id="291a1-109">**方法**</span><span class="sxs-lookup"><span data-stu-id="291a1-109">**Method**</span></span>  
 <span data-ttu-id="291a1-110">从列表中为要执行的任务选择 Web 方法。</span><span class="sxs-lookup"><span data-stu-id="291a1-110">Select a Web method from the list for the task to execute.</span></span>  
  
 <span data-ttu-id="291a1-111">**WebMethodDocumentation**</span><span class="sxs-lookup"><span data-stu-id="291a1-111">**WebMethodDocumentation**</span></span>  
 <span data-ttu-id="291a1-112">键入对 Web 方法的说明，或单击浏览按钮 (…)，再在“Web 方法文档”对话框中键入说明   。</span><span class="sxs-lookup"><span data-stu-id="291a1-112">Type a description of Web method, or the click the browse button **(...)** and then type the description in the **Web Method Documentation** dialog box.</span></span>  
  
 <span data-ttu-id="291a1-113">**名称**</span><span class="sxs-lookup"><span data-stu-id="291a1-113">**Name**</span></span>  
 <span data-ttu-id="291a1-114">列出为 Web 方法提供的输入名称。</span><span class="sxs-lookup"><span data-stu-id="291a1-114">Lists the names of the inputs to the Web method.</span></span>  
  
 <span data-ttu-id="291a1-115">类型</span><span class="sxs-lookup"><span data-stu-id="291a1-115">**Type**</span></span>  
 <span data-ttu-id="291a1-116">列出输入的数据类型。</span><span class="sxs-lookup"><span data-stu-id="291a1-116">Lists the data type of the inputs.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="291a1-117">Web 服务任务仅支持以下数据类型的参数：Primitive 类型（如 integer 和 string）、Primitive 类型的数组和序列，以及枚举。</span><span class="sxs-lookup"><span data-stu-id="291a1-117">The Web Service task supports parameters of the following data types only: primitive types such as integers and strings; arrays and sequences of primitive types; and enumerations.</span></span>  
  
 <span data-ttu-id="291a1-118">**变量**</span><span class="sxs-lookup"><span data-stu-id="291a1-118">**Variable**</span></span>  
 <span data-ttu-id="291a1-119">选中该复选框以使用变量来提供输入。</span><span class="sxs-lookup"><span data-stu-id="291a1-119">Select the check boxes to use variables to provide inputs.</span></span>  
  
 <span data-ttu-id="291a1-120">**值**</span><span class="sxs-lookup"><span data-stu-id="291a1-120">**Value**</span></span>  
 <span data-ttu-id="291a1-121">如果选中了“变量”复选框，则请在列表中选择要提供输入的变量；否则，请键入要在输入中使用的值。</span><span class="sxs-lookup"><span data-stu-id="291a1-121">If the Variable check-boxes are selected, select the variables in the list to provide the inputs; otherwise, type the values to use in the inputs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="291a1-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="291a1-122">See Also</span></span>  
 <span data-ttu-id="291a1-123">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="291a1-123">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="291a1-124">[Web 服务任务编辑器 &#40;常规 "页面&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="291a1-124">[Web Service Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="291a1-125">[Web 服务任务编辑器 &#40;输出页&#41;](../../2014/integration-services/web-service-task-editor-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="291a1-125">[Web Service Task Editor &#40;Output Page&#41;](../../2014/integration-services/web-service-task-editor-output-page.md) </span></span>  
 [<span data-ttu-id="291a1-126">“表达式”页</span><span class="sxs-lookup"><span data-stu-id="291a1-126">Expressions Page</span></span>](expressions/expressions-page.md)  
  
  
