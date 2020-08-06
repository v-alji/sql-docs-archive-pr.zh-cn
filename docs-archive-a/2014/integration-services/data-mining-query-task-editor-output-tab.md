---
title: 数据挖掘查询任务编辑器 (输出选项卡) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dmquerytask.output.f1
helpviewer_keywords:
- Data Mining Query Task Editor
ms.assetid: 62f9e015-6fe0-4396-ad90-3ad51bf00025
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1508972b0487daa90f52af723d58185944a19a58
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692454"
---
# <a name="data-mining-query-task-editor-output-tab"></a><span data-ttu-id="45de1-102">数据挖掘查询任务编辑器（“输出”选项卡）</span><span class="sxs-lookup"><span data-stu-id="45de1-102">Data Mining Query Task Editor (Output Tab)</span></span>
  <span data-ttu-id="45de1-103">可以使用 **“数据挖掘查询任务编辑器”** 对话框的 **“输出”** 选项卡指定预测查询的目标。</span><span class="sxs-lookup"><span data-stu-id="45de1-103">Use the **Output** tab of the **Data Mining Query Task Editor** dialog box to specify the destination of the prediction query.</span></span>  
  
 <span data-ttu-id="45de1-104">若要了解有关在包中实现数据挖掘的详细信息，请参阅 [数据挖掘查询任务](control-flow/data-mining-query-task.md) 和 [数据挖掘解决方案](https://docs.microsoft.com/analysis-services/data-mining/data-mining-solutions)。</span><span class="sxs-lookup"><span data-stu-id="45de1-104">To learn about implementing data mining in packages, see [Data Mining Query Task](control-flow/data-mining-query-task.md) and [Data Mining Solutions](https://docs.microsoft.com/analysis-services/data-mining/data-mining-solutions).</span></span>  
  
## <a name="general-options"></a><span data-ttu-id="45de1-105">常规选项</span><span class="sxs-lookup"><span data-stu-id="45de1-105">General Options</span></span>  
 <span data-ttu-id="45de1-106">**名称**</span><span class="sxs-lookup"><span data-stu-id="45de1-106">**Name**</span></span>  
 <span data-ttu-id="45de1-107">为数据挖掘查询任务提供唯一的名称。</span><span class="sxs-lookup"><span data-stu-id="45de1-107">Provide a unique name for the Data Mining Query task.</span></span> <span data-ttu-id="45de1-108">此名称用作任务图标中的标签。</span><span class="sxs-lookup"><span data-stu-id="45de1-108">This name is used as the label in the task icon.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="45de1-109">任务名称在一个包内必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="45de1-109">Task names must be unique within a package.</span></span>  
  
 <span data-ttu-id="45de1-110">**说明**</span><span class="sxs-lookup"><span data-stu-id="45de1-110">**Description**</span></span>  
 <span data-ttu-id="45de1-111">键入数据挖掘查询任务的说明。</span><span class="sxs-lookup"><span data-stu-id="45de1-111">Type a description of the Data Mining Query task.</span></span>  
  
## <a name="output-tab-options"></a><span data-ttu-id="45de1-112">“输出”选项卡选项</span><span class="sxs-lookup"><span data-stu-id="45de1-112">Output Tab Options</span></span>  
 <span data-ttu-id="45de1-113">**Connection**</span><span class="sxs-lookup"><span data-stu-id="45de1-113">**Connection**</span></span>  
 <span data-ttu-id="45de1-114">从列表中选择连接管理器，或单击“新建”\*\*\*\* 以创建新的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="45de1-114">Select a connection manager in the list or click **New** to create a new connection manager.</span></span>  
  
 <span data-ttu-id="45de1-115">**新建**</span><span class="sxs-lookup"><span data-stu-id="45de1-115">**New**</span></span>  
 <span data-ttu-id="45de1-116">创建新的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="45de1-116">Create a new connection manager.</span></span> <span data-ttu-id="45de1-117">只能使用 ADO.NET 和 OLE DB 连接管理器类型。</span><span class="sxs-lookup"><span data-stu-id="45de1-117">Only the ADO.NET and OLE DB connection manager types can be used.</span></span>  
  
 <span data-ttu-id="45de1-118">**输出表**</span><span class="sxs-lookup"><span data-stu-id="45de1-118">**Output table**</span></span>  
 <span data-ttu-id="45de1-119">指定预测查询要将其结果写入的表。</span><span class="sxs-lookup"><span data-stu-id="45de1-119">Specify the table to which the prediction query writes its results.</span></span>  
  
 <span data-ttu-id="45de1-120">**删除并重新创建该输出表**</span><span class="sxs-lookup"><span data-stu-id="45de1-120">**Drop and re-create the output table**</span></span>  
 <span data-ttu-id="45de1-121">指示预测查询是否应通过删除表后再重新创建表来覆盖目标表中的内容。</span><span class="sxs-lookup"><span data-stu-id="45de1-121">Indicate whether the prediction query should overwrite content in the destination table by dropping and then re-creating the table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45de1-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="45de1-122">See Also</span></span>  
 <span data-ttu-id="45de1-123">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="45de1-123">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="45de1-124">[数据挖掘查询任务编辑器 &#40;挖掘模型 "选项卡&#41;](../../2014/integration-services/data-mining-query-task-editor-mining-model-tab.md) </span><span class="sxs-lookup"><span data-stu-id="45de1-124">[Data Mining Query Task Editor &#40;Mining Model Tab&#41;](../../2014/integration-services/data-mining-query-task-editor-mining-model-tab.md) </span></span>  
 <span data-ttu-id="45de1-125">[数据挖掘查询任务编辑器 &#40;查询选项卡&#41;](../../2014/integration-services/data-mining-query-task-editor-query-tab.md) </span><span class="sxs-lookup"><span data-stu-id="45de1-125">[Data Mining Query Task Editor &#40;Query Tab&#41;](../../2014/integration-services/data-mining-query-task-editor-query-tab.md) </span></span>  
 [<span data-ttu-id="45de1-126">Data Mining Designer</span><span class="sxs-lookup"><span data-stu-id="45de1-126">Data Mining Designer</span></span>](https://docs.microsoft.com/analysis-services/data-mining/data-mining-designer)  
  
  
