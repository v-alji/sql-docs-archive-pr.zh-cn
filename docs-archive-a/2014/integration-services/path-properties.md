---
title: 路径属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- paths [Integration Services], properties
ms.assetid: 89b1e347-9579-4f6b-af74-c6519ea08eea
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ca263b866fb6d5d7ceb6352f708f387d79cad4f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578288"
---
# <a name="path-properties"></a><span data-ttu-id="81a01-102">路径属性</span><span class="sxs-lookup"><span data-stu-id="81a01-102">Path Properties</span></span>
  <span data-ttu-id="81a01-103">对象模型中的数据流对象在 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 组件、输入和输出以及输入列和输出列的级别上具有通用属性和自定义属性。</span><span class="sxs-lookup"><span data-stu-id="81a01-103">The data flow objects in the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] object model have common properties and custom properties at the level of the component, inputs and outputs, and input columns and output columns.</span></span> <span data-ttu-id="81a01-104">其中许多属性的值是只读的，由数据流引擎在运行时分配。</span><span class="sxs-lookup"><span data-stu-id="81a01-104">Many properties have read-only values that are assigned at run time by the data flow engine.</span></span>  
  
 <span data-ttu-id="81a01-105">本主题列出并描述了连接数据流对象的路径的自定义属性。</span><span class="sxs-lookup"><span data-stu-id="81a01-105">This topic lists and describes the custom properties of the paths that connect data flow objects.</span></span>  
  
## <a name="path-properties"></a><span data-ttu-id="81a01-106">路径属性</span><span class="sxs-lookup"><span data-stu-id="81a01-106">Path Properties</span></span>  
 <span data-ttu-id="81a01-107">在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 对象模型中，数据流中连接组件的路径实现 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> 接口。</span><span class="sxs-lookup"><span data-stu-id="81a01-107">In the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] object model, a path that connects components in the data flow implements the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> interface.</span></span>  
  
 <span data-ttu-id="81a01-108">下表介绍了数据流中路径的可配置属性。</span><span class="sxs-lookup"><span data-stu-id="81a01-108">The following table describes the configurable properties of the paths in a data flow.</span></span> <span data-ttu-id="81a01-109">数据流引擎还为此处未列出的其他只读属性赋值。</span><span class="sxs-lookup"><span data-stu-id="81a01-109">The data flow engine also assigns values to additional read-only properties that are not listed here.</span></span>  
  
|<span data-ttu-id="81a01-110">属性名称</span><span class="sxs-lookup"><span data-stu-id="81a01-110">Property name</span></span>|<span data-ttu-id="81a01-111">数据类型</span><span class="sxs-lookup"><span data-stu-id="81a01-111">Data Type</span></span>|<span data-ttu-id="81a01-112">说明</span><span class="sxs-lookup"><span data-stu-id="81a01-112">Description</span></span>|  
|-------------------|---------------|-----------------|  
|<span data-ttu-id="81a01-113">PathAnnotation</span><span class="sxs-lookup"><span data-stu-id="81a01-113">PathAnnotation</span></span>|<span data-ttu-id="81a01-114">Integer（枚举）</span><span class="sxs-lookup"><span data-stu-id="81a01-114">Integer (enumeration)</span></span>|<span data-ttu-id="81a01-115">用于指示在设计器图面上显示路径时是否应显示批注的值。</span><span class="sxs-lookup"><span data-stu-id="81a01-115">A value that indicates whether an annotation should be displayed with the path on the designer surface.</span></span> <span data-ttu-id="81a01-116">可能的值为 `AsNeeded`、`SourceName`、`PathName` 和 `Never`。</span><span class="sxs-lookup"><span data-stu-id="81a01-116">The possible values are `AsNeeded`, `SourceName`, `PathName`, and `Never`.</span></span> <span data-ttu-id="81a01-117">默认值为 `AsNeeded`。</span><span class="sxs-lookup"><span data-stu-id="81a01-117">The default value is `AsNeeded`.</span></span>|  
|<span data-ttu-id="81a01-118">DestinationName</span><span class="sxs-lookup"><span data-stu-id="81a01-118">DestinationName</span></span>|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100>|<span data-ttu-id="81a01-119">与路径关联的输入。</span><span class="sxs-lookup"><span data-stu-id="81a01-119">The input associated with the path.</span></span>|  
|<span data-ttu-id="81a01-120">SourceName</span><span class="sxs-lookup"><span data-stu-id="81a01-120">SourceName</span></span>|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100>|<span data-ttu-id="81a01-121">与路径关联的输出。</span><span class="sxs-lookup"><span data-stu-id="81a01-121">The output associated with the path.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="81a01-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="81a01-122">See Also</span></span>  
 <span data-ttu-id="81a01-123">[Integration Services 路径](data-flow/integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="81a01-123">[Integration Services Paths](data-flow/integration-services-paths.md) </span></span>  
 <span data-ttu-id="81a01-124">[通用属性](../../2014/integration-services/common-properties.md) </span><span class="sxs-lookup"><span data-stu-id="81a01-124">[Common Properties](../../2014/integration-services/common-properties.md) </span></span>  
 <span data-ttu-id="81a01-125">[转换自定义属性](data-flow/transformations/transformation-custom-properties.md) </span><span class="sxs-lookup"><span data-stu-id="81a01-125">[Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md) </span></span>  
 [<span data-ttu-id="81a01-126">可以使用表达式设置的数据流属性</span><span class="sxs-lookup"><span data-stu-id="81a01-126">Data Flow Properties that Can Be Set by Using Expressions</span></span>](../../2014/integration-services/data-flow-properties-that-can-be-set-by-using-expressions.md)  
  
  
