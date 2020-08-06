---
title: 分区处理目标编辑器 (映射页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.partprocessingtransformation.mapping.f1
helpviewer_keywords:
- Partition Processing Destination Editor
ms.assetid: e75b766c-85ba-453e-9576-4a1a34f91ecc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3855b15c7ebf1f6fa95c941931869064d552680e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590274"
---
# <a name="partition-processing-destination-editor-mappings-page"></a><span data-ttu-id="e4221-102">分区处理目标编辑器（“映射”页）</span><span class="sxs-lookup"><span data-stu-id="e4221-102">Partition Processing Destination Editor (Mappings Page)</span></span>
  <span data-ttu-id="e4221-103">可以使用 **“分区处理目标编辑器”** 对话框的 **“映射”** 页，将输入列映射到分区列。</span><span class="sxs-lookup"><span data-stu-id="e4221-103">Use the **Mappings** page of the **Partition Processing Destination Editor** dialog box to map input columns to partition columns.</span></span>  
  
 <span data-ttu-id="e4221-104">若要了解有关分区处理目标的详细信息，请参阅 [Partition Processing Destination](data-flow/partition-processing-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="e4221-104">To learn more abou the Partition Processing destination, see [Partition Processing Destination](data-flow/partition-processing-destination.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e4221-105">此处所述的任何不适用于 Analysis Services 表格模型。</span><span class="sxs-lookup"><span data-stu-id="e4221-105">Tasks described here do not apply to Analysis Services tabular models.</span></span>  <span data-ttu-id="e4221-106">你无法将输入列映射到表格模型的分区列。</span><span class="sxs-lookup"><span data-stu-id="e4221-106">You cannot map input columns to partition columns for tabular models.</span></span> <span data-ttu-id="e4221-107">您可以改用 [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md) 处理分区。</span><span class="sxs-lookup"><span data-stu-id="e4221-107">You can instead use the Analysis Services Execute DDL task [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md) to process the partition.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e4221-108">选项</span><span class="sxs-lookup"><span data-stu-id="e4221-108">Options</span></span>  
 <span data-ttu-id="e4221-109">**可用输入列**</span><span class="sxs-lookup"><span data-stu-id="e4221-109">**Available Input Columns**</span></span>  
 <span data-ttu-id="e4221-110">查看可用输入列的列表。</span><span class="sxs-lookup"><span data-stu-id="e4221-110">View the list of available input columns.</span></span> <span data-ttu-id="e4221-111">使用拖放操作可以将表中的可用输入列映射到目标列。</span><span class="sxs-lookup"><span data-stu-id="e4221-111">Use a drag-and-drop operation to map available input columns in the table to destination columns.</span></span>  
  
 <span data-ttu-id="e4221-112">**可用目标列**</span><span class="sxs-lookup"><span data-stu-id="e4221-112">**Available Destination Columns**</span></span>  
 <span data-ttu-id="e4221-113">查看可用目标列的列表。</span><span class="sxs-lookup"><span data-stu-id="e4221-113">View the list of available destination columns.</span></span> <span data-ttu-id="e4221-114">使用拖放操作可以将表中的可用目标列映射到输入列。</span><span class="sxs-lookup"><span data-stu-id="e4221-114">Use a drag-and-drop operation to map available destination columns in the table to input columns.</span></span>  
  
 <span data-ttu-id="e4221-115">**输入列**</span><span class="sxs-lookup"><span data-stu-id="e4221-115">**Input Column**</span></span>  
 <span data-ttu-id="e4221-116">查看从上表中选择的输入列。</span><span class="sxs-lookup"><span data-stu-id="e4221-116">View input columns selected from the table above.</span></span> <span data-ttu-id="e4221-117">可以通过使用 **“可用输入列”** 列表来更改映射。</span><span class="sxs-lookup"><span data-stu-id="e4221-117">You can change the mappings by using the list of **Available Input Columns**.</span></span>  
  
 <span data-ttu-id="e4221-118">**目标列**</span><span class="sxs-lookup"><span data-stu-id="e4221-118">**Destination Column**</span></span>  
 <span data-ttu-id="e4221-119">查看每个可用的目标列，包括已映射或未映射的目标列。</span><span class="sxs-lookup"><span data-stu-id="e4221-119">View each available destination column, whether it is mapped or not.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4221-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e4221-120">See Also</span></span>  
 <span data-ttu-id="e4221-121">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="e4221-121">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="e4221-122">[分区处理目标编辑器 &#40;连接管理器页&#41;](../../2014/integration-services/partition-processing-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="e4221-122">[Partition Processing Destination Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/partition-processing-destination-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="e4221-123">分区处理目标编辑器（“高级”页）</span><span class="sxs-lookup"><span data-stu-id="e4221-123">Partition Processing Destination Editor &#40;Advanced Page&#41;</span></span>](../../2014/integration-services/partition-processing-destination-editor-advanced-page.md)  
  
  
