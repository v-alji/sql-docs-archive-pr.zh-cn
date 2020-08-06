---
title: Web 服务任务编辑器 (输出页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.webservicestask.output.f1
helpviewer_keywords:
- Web Service Task Editor
ms.assetid: 73c83969-7b0e-479d-a436-0a46b2068d01
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6ad034ae78a096ebe5998ac2c3d2573fe7c3bfd4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590262"
---
# <a name="web-service-task-editor-output-page"></a><span data-ttu-id="228ba-102">Web 服务任务编辑器（“输出”页）</span><span class="sxs-lookup"><span data-stu-id="228ba-102">Web Service Task Editor (Output Page)</span></span>
  <span data-ttu-id="228ba-103">可以使用 **“Web 服务任务编辑器”** 对话框的 **“输出”** 页，指定 Web 方法返回的结果的存储位置。</span><span class="sxs-lookup"><span data-stu-id="228ba-103">Use the **Output** page of the **Web Service Task Editor** dialog box to specify where to store the result returned by the Web method.</span></span>  
  
 <span data-ttu-id="228ba-104">若要了解此任务，请参阅 [Web 服务任务](control-flow/web-service-task.md)。</span><span class="sxs-lookup"><span data-stu-id="228ba-104">To learn about this task, see [Web Service Task](control-flow/web-service-task.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="228ba-105">静态选项</span><span class="sxs-lookup"><span data-stu-id="228ba-105">Static Options</span></span>  
 <span data-ttu-id="228ba-106">**OutputType**</span><span class="sxs-lookup"><span data-stu-id="228ba-106">**OutputType**</span></span>  
 <span data-ttu-id="228ba-107">选择存储结果时所使用的存储类型。</span><span class="sxs-lookup"><span data-stu-id="228ba-107">Select the storage type to use when storing the results.</span></span> <span data-ttu-id="228ba-108">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="228ba-108">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="228ba-109">值</span><span class="sxs-lookup"><span data-stu-id="228ba-109">Value</span></span>|<span data-ttu-id="228ba-110">说明</span><span class="sxs-lookup"><span data-stu-id="228ba-110">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="228ba-111">**文件连接**</span><span class="sxs-lookup"><span data-stu-id="228ba-111">**File Connection**</span></span>|<span data-ttu-id="228ba-112">将结果存储在文件中。</span><span class="sxs-lookup"><span data-stu-id="228ba-112">Store the results in a file.</span></span> <span data-ttu-id="228ba-113">选择此值将显示动态选项 **File**。</span><span class="sxs-lookup"><span data-stu-id="228ba-113">Selecting this value displays the dynamic option, **File**.</span></span>|  
|<span data-ttu-id="228ba-114">**变量**</span><span class="sxs-lookup"><span data-stu-id="228ba-114">**Variable**</span></span>|<span data-ttu-id="228ba-115">将结果存储在变量中。</span><span class="sxs-lookup"><span data-stu-id="228ba-115">Store the results in a variable.</span></span> <span data-ttu-id="228ba-116">选择此值将显示动态选项 **Variable**。</span><span class="sxs-lookup"><span data-stu-id="228ba-116">Selecting this value displays the dynamic option, **Variable**.</span></span>|  
  
## <a name="outputtype-dynamic-options"></a><span data-ttu-id="228ba-117">OutputType 动态选项</span><span class="sxs-lookup"><span data-stu-id="228ba-117">OutputType Dynamic Options</span></span>  
  
### <a name="outputtype--file-connection"></a><span data-ttu-id="228ba-118">OutputType = 文件连接</span><span class="sxs-lookup"><span data-stu-id="228ba-118">OutputType = File Connection</span></span>  
 <span data-ttu-id="228ba-119">**File**</span><span class="sxs-lookup"><span data-stu-id="228ba-119">**File**</span></span>  
 <span data-ttu-id="228ba-120">从列表中选择“文件连接管理器”，或单击“\<**New Connection...**>”创建新的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="228ba-120">Select a File connection manager in the list or click \<**New Connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="228ba-121">**相关主题：** [文件连接管理器](connection-manager/file-connection-manager.md)、[文件连接管理器编辑器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="228ba-121">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
### <a name="outputtype--variable"></a><span data-ttu-id="228ba-122">OutputType = 变量</span><span class="sxs-lookup"><span data-stu-id="228ba-122">OutputType = Variable</span></span>  
 <span data-ttu-id="228ba-123">**变量**</span><span class="sxs-lookup"><span data-stu-id="228ba-123">**Variable**</span></span>  
 <span data-ttu-id="228ba-124">在列表中选择变量，或单击“\<**New Variable...**>”创建新变量。</span><span class="sxs-lookup"><span data-stu-id="228ba-124">Select a variable in the list or click \<**New Variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="228ba-125">**相关主题：** [Integration Services &#40;SSIS&#41; 变量](integration-services-ssis-variables.md)、[添加变量](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="228ba-125">**Related Topics:**  [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="228ba-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="228ba-126">See Also</span></span>  
 <span data-ttu-id="228ba-127">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="228ba-127">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="228ba-128">[Web 服务任务编辑器 &#40;常规 "页面&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="228ba-128">[Web Service Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="228ba-129">[Web 服务任务编辑器 &#40;输入页&#41;](../../2014/integration-services/web-service-task-editor-input-page.md) </span><span class="sxs-lookup"><span data-stu-id="228ba-129">[Web Service Task Editor &#40;Input Page&#41;](../../2014/integration-services/web-service-task-editor-input-page.md) </span></span>  
 [<span data-ttu-id="228ba-130">“表达式”页</span><span class="sxs-lookup"><span data-stu-id="228ba-130">Expressions Page</span></span>](expressions/expressions-page.md)  
  
  
