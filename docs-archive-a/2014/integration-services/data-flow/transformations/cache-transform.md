---
title: 缓存转换 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.cachetrans.f1
helpviewer_keywords:
- Cache transform
ms.assetid: a5683fc8-9c32-4634-819e-e9815627e4f1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 34be3252a3caf344c95e13ae45cc485a8c4ffdc7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587945"
---
# <a name="cache-transform"></a><span data-ttu-id="e87c6-102">缓存转换</span><span class="sxs-lookup"><span data-stu-id="e87c6-102">Cache Transform</span></span>
  <span data-ttu-id="e87c6-103">“缓存转换”转换通过将所连接数据源中的数据写入流入缓存连接管理器的数据流，可以为查找转换生成一个引用数据集。</span><span class="sxs-lookup"><span data-stu-id="e87c6-103">The Cache Transform transformation generates a reference dataset for the Lookup Transformation by writing data from a connected data source in the data flow to a Cache connection manager.</span></span> <span data-ttu-id="e87c6-104">查找转换通过将所连接数据源输入列中的数据与引用数据库中的列进行联接来执行查找。</span><span class="sxs-lookup"><span data-stu-id="e87c6-104">The Lookup transformation performs lookups by joining data in input columns from a connected data source with columns in the reference database.</span></span>  
  
 <span data-ttu-id="e87c6-105">若想将查找转换配置为在完全缓存模式中运行，可使用缓存连接管理器。</span><span class="sxs-lookup"><span data-stu-id="e87c6-105">You can use the Cache connection manager when you want to configure the Lookup Transformation to run in the full cache mode.</span></span> <span data-ttu-id="e87c6-106">在此模式下，在查找转换运行前，引用数据集会加载到缓存中。</span><span class="sxs-lookup"><span data-stu-id="e87c6-106">In this mode, the reference dataset is loaded into cache before the Lookup Transformation runs.</span></span>  
  
 <span data-ttu-id="e87c6-107">有关如何使用缓存连接管理器和“缓存转换”转换配置完全缓存模式下的查找转换的说明，请参阅 [在完全缓存模式下使用缓存连接管理器实现查找转换](../../connection-manager/lookup-transformation-full-cache-mode-ole-db-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="e87c6-107">For instructions on how to configure the Lookup transformation in full cache mode with the Cache connection manager and Cache Transform transformation, see [Implement a Lookup Transformation in Full Cache Mode Using the Cache Connection Manager](../../connection-manager/lookup-transformation-full-cache-mode-ole-db-connection-manager.md).</span></span>  
  
 <span data-ttu-id="e87c6-108">有关缓存引用数据集的详细信息，请参阅 [Lookup Transformation](lookup-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="e87c6-108">For more information on caching the reference dataset, see [Lookup Transformation](lookup-transformation.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e87c6-109">“缓存转换”仅向缓存连接管理器写入唯一行。</span><span class="sxs-lookup"><span data-stu-id="e87c6-109">The Cache Transform writes only unique rows to the Cache connection manager.</span></span>  
  
 <span data-ttu-id="e87c6-110">在单个包中，只有一个缓存转换可以将数据写入同一缓存连接管理器。</span><span class="sxs-lookup"><span data-stu-id="e87c6-110">In a single package, only one Cache Transform can write data to the same Cache connection manager.</span></span> <span data-ttu-id="e87c6-111">如果某个包中包含多个缓存转换，则该包在运行时所调用的第一个缓存转换会将数据写入连接管理器。</span><span class="sxs-lookup"><span data-stu-id="e87c6-111">If the package contains multiple Cache Transforms, the first Cache Transform that is called when the package runs, writes the data to the connection manager.</span></span> <span data-ttu-id="e87c6-112">后续缓存转换将无法执行写入操作。</span><span class="sxs-lookup"><span data-stu-id="e87c6-112">The write operations of subsequent Cache Transforms fail.</span></span>  
  
 <span data-ttu-id="e87c6-113">有关详细信息，请参阅 [Cache Connection Manager](../../connection-manager/cache-connection-manager.md) 和 [Cache Connection Manager Editor](../../cache-connection-manager-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="e87c6-113">For more information, see [Cache Connection Manager](../../connection-manager/cache-connection-manager.md) and [Cache Connection Manager Editor](../../cache-connection-manager-editor.md).</span></span>  
  
## <a name="configuration-of-the-cache-transform"></a><span data-ttu-id="e87c6-114">缓存转换的配置</span><span class="sxs-lookup"><span data-stu-id="e87c6-114">Configuration of the Cache Transform</span></span>  
 <span data-ttu-id="e87c6-115">可以将缓存连接管理器配置为向缓存文件 (.caw) 中保存数据。</span><span class="sxs-lookup"><span data-stu-id="e87c6-115">You can configure the Cache connection manager to save the data to a cache file (.caw).</span></span>  
  
 <span data-ttu-id="e87c6-116">可以采用下列方法配置缓存转换：</span><span class="sxs-lookup"><span data-stu-id="e87c6-116">You can configure the Cache Transform in the following ways:</span></span>  
  
-   <span data-ttu-id="e87c6-117">指定缓存连接管理器。</span><span class="sxs-lookup"><span data-stu-id="e87c6-117">Specify the Cache connection manager.</span></span>  
  
-   <span data-ttu-id="e87c6-118">将缓存转换中的输入列映射到缓存连接管理器中的目标列。</span><span class="sxs-lookup"><span data-stu-id="e87c6-118">Map the input columns in the Cache Transform to destination columns in the Cache connection manager.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e87c6-119">每个输入列都必须映射到目标列，而且二者的列数据类型必须匹配。</span><span class="sxs-lookup"><span data-stu-id="e87c6-119">Each input column must be mapped to a destination column, and the column data types must match.</span></span> <span data-ttu-id="e87c6-120">否则， [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 设计器将显示一则错误消息。</span><span class="sxs-lookup"><span data-stu-id="e87c6-120">Otherwise, [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] Designer displays an error message.</span></span>  
  
     <span data-ttu-id="e87c6-121">可以使用 **“缓存连接管理器编辑器”** 修改列数据类型、名称以及其他列属性。</span><span class="sxs-lookup"><span data-stu-id="e87c6-121">You can use the **Cache Connection Manager Editor** to modify column data types, names, and other column properties.</span></span>  
  
 <span data-ttu-id="e87c6-122">可以通过 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 设计器来设置属性。</span><span class="sxs-lookup"><span data-stu-id="e87c6-122">You can set properties through [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] Designer.</span></span> <span data-ttu-id="e87c6-123">有关可在 **“高级编辑器”** 对话框中设置的属性的详细信息，请参阅 [Transformation Custom Properties](transformation-custom-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="e87c6-123">For more information about the properties that you can set in the **Advanced Editor** dialog box, see [Transformation Custom Properties](transformation-custom-properties.md).</span></span>  
  
 <span data-ttu-id="e87c6-124">有关如何设置属性的详细信息，请参阅 [设置数据流组件的属性](../set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="e87c6-124">For more information about how to set properties, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e87c6-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e87c6-125">See Also</span></span>  
 <span data-ttu-id="e87c6-126">[Integration Services 转换](integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="e87c6-126">[Integration Services Transformations](integration-services-transformations.md) </span></span>  
 [<span data-ttu-id="e87c6-127">数据流</span><span class="sxs-lookup"><span data-stu-id="e87c6-127">Data Flow</span></span>](../data-flow.md)  
  
  
