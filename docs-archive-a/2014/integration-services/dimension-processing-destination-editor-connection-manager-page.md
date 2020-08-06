---
title: 维度处理目标编辑器 (连接管理器页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dimprocessingtransformation.connection.f1
helpviewer_keywords:
- Dimension Processing Destination Editor
ms.assetid: 44aab631-d62d-4895-8fc7-7f1f3b1b68ce
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 50ba42292c1f48c9b1cdf2ba00c709dacd2f9675
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590929"
---
# <a name="dimension-processing-destination-editor-connection-manager-page"></a><span data-ttu-id="50708-102">维度处理目标编辑器（“连接管理器”页）</span><span class="sxs-lookup"><span data-stu-id="50708-102">Dimension Processing Destination Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="50708-103">可以使用“维度处理目标编辑器”对话框的“连接管理器”页面指定与 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 项目或 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例之间的连接\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="50708-103">Use the **Connection Manager** page of the **Dimension Processing Destination Editor** dialog box to specify a connection to a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project or to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="50708-104">若要了解有关维度处理目标的详细信息，请参阅 [Dimension Processing Destination](data-flow/dimension-processing-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="50708-104">To learn more about the Dimension Processing destination, see [Dimension Processing Destination](data-flow/dimension-processing-destination.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="50708-105">选项</span><span class="sxs-lookup"><span data-stu-id="50708-105">Options</span></span>  
 <span data-ttu-id="50708-106">**“ODBC 目标编辑器”**</span><span class="sxs-lookup"><span data-stu-id="50708-106">**Connection manager**</span></span>  
 <span data-ttu-id="50708-107">从列表中选择现有连接管理器，或单击“新建”\*\*\*\* 创建新的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="50708-107">Select an existing connection manager from the list, or click **New** to create a new connection manager.</span></span>  
  
 <span data-ttu-id="50708-108">**新建**</span><span class="sxs-lookup"><span data-stu-id="50708-108">**New**</span></span>  
 <span data-ttu-id="50708-109">通过使用“添加 Analysis Services 连接管理器”\*\*\*\* 对话框创建一个新连接。</span><span class="sxs-lookup"><span data-stu-id="50708-109">Create a new connection by using the **Add Analysis Services Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="50708-110">**可用维度列表**</span><span class="sxs-lookup"><span data-stu-id="50708-110">**List of available dimensions**</span></span>  
 <span data-ttu-id="50708-111">选择要处理的维度。</span><span class="sxs-lookup"><span data-stu-id="50708-111">Select the dimension to process.</span></span>  
  
 <span data-ttu-id="50708-112">**处理方法**</span><span class="sxs-lookup"><span data-stu-id="50708-112">**Processing method**</span></span>  
 <span data-ttu-id="50708-113">选择要应用于列表中选定维度的处理方法。</span><span class="sxs-lookup"><span data-stu-id="50708-113">Select the processing method to apply to the dimension selected in the list.</span></span> <span data-ttu-id="50708-114">此选项的默认值为 **“完全”**。</span><span class="sxs-lookup"><span data-stu-id="50708-114">The default value of this option is **Full**.</span></span>  
  
|<span data-ttu-id="50708-115">值</span><span class="sxs-lookup"><span data-stu-id="50708-115">Value</span></span>|<span data-ttu-id="50708-116">说明</span><span class="sxs-lookup"><span data-stu-id="50708-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="50708-117">**添加(增量式)**</span><span class="sxs-lookup"><span data-stu-id="50708-117">**Add (incremental)**</span></span>|<span data-ttu-id="50708-118">对维度执行增量处理。</span><span class="sxs-lookup"><span data-stu-id="50708-118">Perform an incremental processing of the dimension.</span></span>|  
|<span data-ttu-id="50708-119">**完整**</span><span class="sxs-lookup"><span data-stu-id="50708-119">**Full**</span></span>|<span data-ttu-id="50708-120">对维度执行完全处理。</span><span class="sxs-lookup"><span data-stu-id="50708-120">Perform full processing of the dimension.</span></span>|  
|<span data-ttu-id="50708-121">**更新**</span><span class="sxs-lookup"><span data-stu-id="50708-121">**Update**</span></span>|<span data-ttu-id="50708-122">对维度执行更新处理。</span><span class="sxs-lookup"><span data-stu-id="50708-122">Perform an update processing of the dimension.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="50708-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="50708-123">See Also</span></span>  
 <span data-ttu-id="50708-124">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="50708-124">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="50708-125">[维度处理目标编辑器 &#40;映射 "页面&#41;](../../2014/integration-services/dimension-processing-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="50708-125">[Dimension Processing Destination Editor &#40;Mappings Page&#41;](../../2014/integration-services/dimension-processing-destination-editor-mappings-page.md) </span></span>  
 [<span data-ttu-id="50708-126">维度处理目标编辑器（“高级”页）</span><span class="sxs-lookup"><span data-stu-id="50708-126">Dimension Processing Destination Editor &#40;Advanced Page&#41;</span></span>](../../2014/integration-services/dimension-processing-destination-editor-advanced-page.md)  
  
  
