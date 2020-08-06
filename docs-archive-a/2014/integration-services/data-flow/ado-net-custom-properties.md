---
title: ADO NET 自定义属性 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: e062a9ab-1e6b-4061-845a-4f8a0552b09d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bada6f512770d0f9f07ddc3693070c8aad309cb5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682999"
---
# <a name="ado-net-custom-properties"></a><span data-ttu-id="94cd1-102">ADO NET 自定义属性</span><span class="sxs-lookup"><span data-stu-id="94cd1-102">ADO NET Custom Properties</span></span>
  <span data-ttu-id="94cd1-103">**源自定义属性**</span><span class="sxs-lookup"><span data-stu-id="94cd1-103">**Source Custom Properties**</span></span>  
  
 <span data-ttu-id="94cd1-104">ADO NET 源具有自定义属性和所有数据流组件共有的属性。</span><span class="sxs-lookup"><span data-stu-id="94cd1-104">The ADO NET source has both custom properties and the properties common to all data flow components.</span></span>  
  
 <span data-ttu-id="94cd1-105">下表介绍 ADO NET 源的自定义属性。</span><span class="sxs-lookup"><span data-stu-id="94cd1-105">The following table describes the custom properties of the ADO NET source.</span></span> <span data-ttu-id="94cd1-106">所有属性均可读/写。</span><span class="sxs-lookup"><span data-stu-id="94cd1-106">All properties are read/write.</span></span>  
  
|<span data-ttu-id="94cd1-107">属性名称</span><span class="sxs-lookup"><span data-stu-id="94cd1-107">Property name</span></span>|<span data-ttu-id="94cd1-108">数据类型</span><span class="sxs-lookup"><span data-stu-id="94cd1-108">Data Type</span></span>|<span data-ttu-id="94cd1-109">说明</span><span class="sxs-lookup"><span data-stu-id="94cd1-109">Description</span></span>|  
|-------------------|---------------|-----------------|  
|<span data-ttu-id="94cd1-110">CommandTimeout</span><span class="sxs-lookup"><span data-stu-id="94cd1-110">CommandTimeout</span></span>|<span data-ttu-id="94cd1-111">String</span><span class="sxs-lookup"><span data-stu-id="94cd1-111">String</span></span>|<span data-ttu-id="94cd1-112">该值指定 SQL 命令超时之前等待的秒数。值为 0 时指示命令永远不会超时。</span><span class="sxs-lookup"><span data-stu-id="94cd1-112">A value that specifies the number of seconds before the SQL command times out. A value of 0 indicates that the command never times out.</span></span>|  
|<span data-ttu-id="94cd1-113">SqlCommand</span><span class="sxs-lookup"><span data-stu-id="94cd1-113">SqlCommand</span></span>|<span data-ttu-id="94cd1-114">String</span><span class="sxs-lookup"><span data-stu-id="94cd1-114">String</span></span>|<span data-ttu-id="94cd1-115">ADO NET 源可以用来提取数据的 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="94cd1-115">The SQL statement that the ADO NET source uses to extract data.</span></span><br /><br /> <span data-ttu-id="94cd1-116">当包加载时，可以使用 ADO NET 源将使用的 SQL 语句动态更新此属性。</span><span class="sxs-lookup"><span data-stu-id="94cd1-116">When the package loads, you can dynamically update this property with the SQL statement that the ADO NET source will use.</span></span> <span data-ttu-id="94cd1-117">有关详细信息，请参阅 [Integration Services (SSIS) 表达式](../expressions/integration-services-ssis-expressions.md)和[在包中使用属性表达式](../expressions/use-property-expressions-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="94cd1-117">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../expressions/integration-services-ssis-expressions.md) and [Use Property Expressions in Packages](../expressions/use-property-expressions-in-packages.md).</span></span>|  
|<span data-ttu-id="94cd1-118">AllowImplicitStringConversion</span><span class="sxs-lookup"><span data-stu-id="94cd1-118">AllowImplicitStringConversion</span></span>|<span data-ttu-id="94cd1-119">Boolean</span><span class="sxs-lookup"><span data-stu-id="94cd1-119">Boolean</span></span>|<span data-ttu-id="94cd1-120">该值指示是否出现以下情况：</span><span class="sxs-lookup"><span data-stu-id="94cd1-120">A value that indicates whether the following occurs:</span></span><br /><br /> <span data-ttu-id="94cd1-121">在外部元数据类型与字符串输出列类型（DT_WSTR 或 DT_NTEXT）之间存在不匹配时，未生成验证错误。</span><span class="sxs-lookup"><span data-stu-id="94cd1-121">No generation of a validation error if there is a mismatch between external metadata types and output column types that are strings (DT_WSTR or DT_NTEXT).</span></span><br /><br /> <span data-ttu-id="94cd1-122">外部元数据类型隐式转换为输出列使用的字符串数据类型。</span><span class="sxs-lookup"><span data-stu-id="94cd1-122">Implicit conversion of external metadata types to the string data type that the output column uses.</span></span><br /><br /> <br /><br /> <span data-ttu-id="94cd1-123">默认值为 TRUE。</span><span class="sxs-lookup"><span data-stu-id="94cd1-123">The default value is TRUE.</span></span><br /><br /> <span data-ttu-id="94cd1-124">有关详细信息，请参阅 [ADO NET Source](ado-net-source.md)。</span><span class="sxs-lookup"><span data-stu-id="94cd1-124">For more information, see [ADO NET Source](ado-net-source.md).</span></span>|  
  
 <span data-ttu-id="94cd1-125">ADO NET 源的输出和输出列没有自定义属性。</span><span class="sxs-lookup"><span data-stu-id="94cd1-125">The output and the output columns of the ADO NET source have no custom properties.</span></span>  
  
 <span data-ttu-id="94cd1-126">有关详细信息，请参阅 [ADO NET Source](ado-net-source.md)。</span><span class="sxs-lookup"><span data-stu-id="94cd1-126">For more information, see [ADO NET Source](ado-net-source.md).</span></span>  
  
 <span data-ttu-id="94cd1-127">**目标自定义属性**</span><span class="sxs-lookup"><span data-stu-id="94cd1-127">**Destination Custom Properties**</span></span>  
  
 <span data-ttu-id="94cd1-128">[!INCLUDE[vstecado](../../includes/vstecado-md.md)] 目标具有自定义属性和所有数据流组件共有的属性。</span><span class="sxs-lookup"><span data-stu-id="94cd1-128">The [!INCLUDE[vstecado](../../includes/vstecado-md.md)] destination has both custom properties and the properties common to all data flow components.</span></span>  
  
 <span data-ttu-id="94cd1-129">下表介绍了 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 目标的自定义属性。</span><span class="sxs-lookup"><span data-stu-id="94cd1-129">The following table describes the custom properties of the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] destination.</span></span> <span data-ttu-id="94cd1-130">所有属性均可读/写。</span><span class="sxs-lookup"><span data-stu-id="94cd1-130">All properties are read/write.</span></span> <span data-ttu-id="94cd1-131">这些属性在 **“ADO NET 目标编辑器”** 中不可用，但可以使用 **“高级编辑器”** 进行设置。</span><span class="sxs-lookup"><span data-stu-id="94cd1-131">These properties are not available in the **ADO NET Destination Editor**, but can be set by using the **Advanced Editor**.</span></span>  
  
|<span data-ttu-id="94cd1-132">properties</span><span class="sxs-lookup"><span data-stu-id="94cd1-132">Property</span></span>|<span data-ttu-id="94cd1-133">数据类型</span><span class="sxs-lookup"><span data-stu-id="94cd1-133">Data Type</span></span>|<span data-ttu-id="94cd1-134">说明</span><span class="sxs-lookup"><span data-stu-id="94cd1-134">Description</span></span>|  
|--------------|---------------|-----------------|  
|<span data-ttu-id="94cd1-135">BatchSize</span><span class="sxs-lookup"><span data-stu-id="94cd1-135">BatchSize</span></span>|<span data-ttu-id="94cd1-136">Integer</span><span class="sxs-lookup"><span data-stu-id="94cd1-136">Integer</span></span>|<span data-ttu-id="94cd1-137">向服务器发送的批中的行数。</span><span class="sxs-lookup"><span data-stu-id="94cd1-137">The number of rows in a batch that is sent to the server.</span></span> <span data-ttu-id="94cd1-138">值 **0** 指示批大小与内部缓冲区大小匹配。</span><span class="sxs-lookup"><span data-stu-id="94cd1-138">A value of **0** indicates that the batch size matches the internal buffer size.</span></span> <span data-ttu-id="94cd1-139">此属性的默认值为 **0**。</span><span class="sxs-lookup"><span data-stu-id="94cd1-139">The default value of this property is **0**.</span></span>|  
|<span data-ttu-id="94cd1-140">CommandTimeOut</span><span class="sxs-lookup"><span data-stu-id="94cd1-140">CommandTimeOut</span></span>|<span data-ttu-id="94cd1-141">Integer</span><span class="sxs-lookup"><span data-stu-id="94cd1-141">Integer</span></span>|<span data-ttu-id="94cd1-142">SQL 命令在超时前可以运行的最大秒数。值 **0** 表示不限制时间。</span><span class="sxs-lookup"><span data-stu-id="94cd1-142">The maximum number of seconds that the SQL command can run before timing out. A value of **0** indicates an infinite time.</span></span> <span data-ttu-id="94cd1-143">此属性的默认值为 **0**。</span><span class="sxs-lookup"><span data-stu-id="94cd1-143">The default value of this property is **0**.</span></span>|  
|<span data-ttu-id="94cd1-144">TableOrViewName</span><span class="sxs-lookup"><span data-stu-id="94cd1-144">TableOrViewName</span></span>|<span data-ttu-id="94cd1-145">String</span><span class="sxs-lookup"><span data-stu-id="94cd1-145">String</span></span>|<span data-ttu-id="94cd1-146">目标表或视图的名称。</span><span class="sxs-lookup"><span data-stu-id="94cd1-146">The name of the destination table or view.</span></span>|  
  
 <span data-ttu-id="94cd1-147">有关详细信息，请参阅 [ADO NET Destination](ado-net-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="94cd1-147">For more information, see [ADO NET Destination](ado-net-destination.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94cd1-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="94cd1-148">See Also</span></span>  
 [<span data-ttu-id="94cd1-149">Common Properties</span><span class="sxs-lookup"><span data-stu-id="94cd1-149">Common Properties</span></span>](../common-properties.md)  
  
  
