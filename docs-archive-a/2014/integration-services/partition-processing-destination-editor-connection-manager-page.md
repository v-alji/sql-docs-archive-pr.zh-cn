---
title: 分区处理目标编辑器 (连接管理器页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.partprocessingtransformation.connection.f1
helpviewer_keywords:
- Partition Processing Destination Editor
ms.assetid: 7add6f82-eed1-47fc-a5d7-7b91f3f24d34
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5a0f79dfcc9c0d98d871a49618f4dabfb8a3bbac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581355"
---
# <a name="partition-processing-destination-editor-connection-manager-page"></a><span data-ttu-id="dd957-102">分区处理目标编辑器（“连接管理器”页）</span><span class="sxs-lookup"><span data-stu-id="dd957-102">Partition Processing Destination Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="dd957-103">使用“分区处理目标编辑器”对话框的“连接管理器”页面，可以指定与 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 项目或 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例之间的连接\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="dd957-103">Use the **Connection Manager** page of the **Partition Processing Destination Editor** dialog box to specify a connection to a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project or to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="dd957-104">若要了解有关分区处理目标的详细信息，请参阅 [Partition Processing Destination](data-flow/partition-processing-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="dd957-104">To learn more abou the Partition Processing destination, see [Partition Processing Destination](data-flow/partition-processing-destination.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dd957-105">此处所述的任何不适用于 Analysis Services 表格模型。</span><span class="sxs-lookup"><span data-stu-id="dd957-105">Tasks described here do not apply to Analysis Services tabular models.</span></span>  <span data-ttu-id="dd957-106">你无法将输入列映射到表格模型的分区列。</span><span class="sxs-lookup"><span data-stu-id="dd957-106">You cannot map input columns to partition columns for tabular models.</span></span> <span data-ttu-id="dd957-107">您可以改用 [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md) 处理分区。</span><span class="sxs-lookup"><span data-stu-id="dd957-107">You can instead use the Analysis Services Execute DDL task [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md) to process the partition.</span></span>  
  
## <a name="options"></a><span data-ttu-id="dd957-108">选项</span><span class="sxs-lookup"><span data-stu-id="dd957-108">Options</span></span>  
 <span data-ttu-id="dd957-109">**“ODBC 目标编辑器”**</span><span class="sxs-lookup"><span data-stu-id="dd957-109">**Connection manager**</span></span>  
 <span data-ttu-id="dd957-110">从列表中选择一个现有连接管理器，或通过单击“新建”  创建一个新连接。</span><span class="sxs-lookup"><span data-stu-id="dd957-110">Select an existing connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="dd957-111">**新建**</span><span class="sxs-lookup"><span data-stu-id="dd957-111">**New**</span></span>  
 <span data-ttu-id="dd957-112">通过使用“添加 Analysis Services 连接管理器”\*\*\*\* 对话框创建一个新连接。</span><span class="sxs-lookup"><span data-stu-id="dd957-112">Create a new connection by using the **Add Analysis Services Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="dd957-113">**可用分区列表**</span><span class="sxs-lookup"><span data-stu-id="dd957-113">**List of available partitions**</span></span>  
 <span data-ttu-id="dd957-114">选择要处理的分区。</span><span class="sxs-lookup"><span data-stu-id="dd957-114">Select the partition to process.</span></span>  
  
 <span data-ttu-id="dd957-115">**处理方法**</span><span class="sxs-lookup"><span data-stu-id="dd957-115">**Processing method**</span></span>  
 <span data-ttu-id="dd957-116">选择处理方法。</span><span class="sxs-lookup"><span data-stu-id="dd957-116">Select the processing method.</span></span> <span data-ttu-id="dd957-117">此选项的默认值为 **“完全”**。</span><span class="sxs-lookup"><span data-stu-id="dd957-117">The default value of this option is **Full**.</span></span>  
  
|<span data-ttu-id="dd957-118">值</span><span class="sxs-lookup"><span data-stu-id="dd957-118">Value</span></span>|<span data-ttu-id="dd957-119">说明</span><span class="sxs-lookup"><span data-stu-id="dd957-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dd957-120">添加(增量式)</span><span class="sxs-lookup"><span data-stu-id="dd957-120">Add (incremental)</span></span>|<span data-ttu-id="dd957-121">对分区执行增量处理。</span><span class="sxs-lookup"><span data-stu-id="dd957-121">Perform an incremental processing of the partition.</span></span>|  
|<span data-ttu-id="dd957-122">完全</span><span class="sxs-lookup"><span data-stu-id="dd957-122">Full</span></span>|<span data-ttu-id="dd957-123">对分区执行完全处理。</span><span class="sxs-lookup"><span data-stu-id="dd957-123">Perform full processing of the partition.</span></span>|  
|<span data-ttu-id="dd957-124">仅限数据</span><span class="sxs-lookup"><span data-stu-id="dd957-124">Data only</span></span>|<span data-ttu-id="dd957-125">对分区执行更新处理。</span><span class="sxs-lookup"><span data-stu-id="dd957-125">Perform an update processing of the partition.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dd957-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dd957-126">See Also</span></span>  
 <span data-ttu-id="dd957-127">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="dd957-127">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="dd957-128">[分区处理目标编辑器 &#40;映射 "页面&#41;](../../2014/integration-services/partition-processing-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="dd957-128">[Partition Processing Destination Editor &#40;Mappings Page&#41;](../../2014/integration-services/partition-processing-destination-editor-mappings-page.md) </span></span>  
 [<span data-ttu-id="dd957-129">分区处理目标编辑器（“高级”页）</span><span class="sxs-lookup"><span data-stu-id="dd957-129">Partition Processing Destination Editor &#40;Advanced Page&#41;</span></span>](../../2014/integration-services/partition-processing-destination-editor-advanced-page.md)  
  
  
