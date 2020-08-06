---
title: 缓存连接管理器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Cache connection manager
ms.assetid: bdc92038-3720-4795-8a5c-79b963f2c952
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b8a7cc8bbe9e93c385fca6257e0be2e79bd3148a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586914"
---
# <a name="cache-connection-manager"></a><span data-ttu-id="d936c-102">缓存连接管理器</span><span class="sxs-lookup"><span data-stu-id="d936c-102">Cache Connection Manager</span></span>
  <span data-ttu-id="d936c-103">缓存连接管理器从缓存转换或从缓存文件 (.caw) 中读取数据，并可将数据保存到缓存文件。</span><span class="sxs-lookup"><span data-stu-id="d936c-103">The Cache connection manager reads data from the Cache transform or from a cache file (.caw), and can save the data to a cache file.</span></span> <span data-ttu-id="d936c-104">无论是否将缓存连接管理器配置为使用缓存文件，数据都会始终存储在内存中。</span><span class="sxs-lookup"><span data-stu-id="d936c-104">Whether you configure the Cache connection manager to use a cache file, the data is always stored in memory.</span></span>  
  
 <span data-ttu-id="d936c-105">“缓存转换”转换可以将数据流中已连接数据源的数据写入缓存连接管理器。</span><span class="sxs-lookup"><span data-stu-id="d936c-105">The Cache Transform transformation writes data from a connected data source in the data flow to a Cache connection manager.</span></span> <span data-ttu-id="d936c-106">包中的查找转换会对数据执行查找。</span><span class="sxs-lookup"><span data-stu-id="d936c-106">The Lookup transformation in a package performs lookups on the data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d936c-107">缓存连接管理器不支持二进制大型对象 (BLOB) 数据类型 DT_TEXT、DT_NTEXT 和 DT_IMAGE。</span><span class="sxs-lookup"><span data-stu-id="d936c-107">The Cache connection manager does not support the Binary Large Object (BLOB) data types DT_TEXT, DT_NTEXT, and DT_IMAGE.</span></span> <span data-ttu-id="d936c-108">如果引用数据集包含 BLOB 数据类型，则运行包时该组件将失败。</span><span class="sxs-lookup"><span data-stu-id="d936c-108">If the reference dataset contains a BLOB data type, the component will fail when you run the package.</span></span> <span data-ttu-id="d936c-109">可以使用 **“缓存连接管理器编辑器”** 修改列数据类型。</span><span class="sxs-lookup"><span data-stu-id="d936c-109">You can use the **Cache Connection Manager Editor** to modify column data types.</span></span> <span data-ttu-id="d936c-110">有关详细信息，请参阅 [Cache Connection Manager Editor](../cache-connection-manager-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="d936c-110">For more information, see [Cache Connection Manager Editor](../cache-connection-manager-editor.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d936c-111">包的保护级别不适用于缓存文件。</span><span class="sxs-lookup"><span data-stu-id="d936c-111">The protection level of the package does not apply to the cache file.</span></span> <span data-ttu-id="d936c-112">如果缓存文件包含敏感信息，可使用访问控制列表 (ACL) 来限制对存储该文件的位置或文件夹的访问。</span><span class="sxs-lookup"><span data-stu-id="d936c-112">If the cache file contains sensitive information, use an access control list (ACL) to restrict access to the location or folder in which you store the file.</span></span> <span data-ttu-id="d936c-113">应只允许访问某些帐户。</span><span class="sxs-lookup"><span data-stu-id="d936c-113">You should enable access only to certain accounts.</span></span> <span data-ttu-id="d936c-114">有关详细信息，请参阅 [访问包使用的文件](../access-to-files-used-by-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="d936c-114">For more information, see [Access to Files Used by Packages](../access-to-files-used-by-packages.md).</span></span>  
  
## <a name="configuration-of-the-cache-connection-manager"></a><span data-ttu-id="d936c-115">缓存连接管理器的配置</span><span class="sxs-lookup"><span data-stu-id="d936c-115">Configuration of the Cache Connection Manager</span></span>  
 <span data-ttu-id="d936c-116">可以用下列方式配置缓存连接管理器：</span><span class="sxs-lookup"><span data-stu-id="d936c-116">You can configure the Cache connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="d936c-117">指示是否使用缓存文件。</span><span class="sxs-lookup"><span data-stu-id="d936c-117">Indicate whether to use a cache file.</span></span>  
  
     <span data-ttu-id="d936c-118">如果将缓存连接管理器配置为使用缓存文件，则连接管理器将执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="d936c-118">If you configure the cache connection manager to use a cache file, the connection manager will do one of the following actions:</span></span>  
  
    -   <span data-ttu-id="d936c-119">若将“缓存转换”转换配置为将数据从数据流中的某个数据源写入缓存连接管理器，则将数据保存到该文件。</span><span class="sxs-lookup"><span data-stu-id="d936c-119">Save data to the file when a Cache Transform transformation is configured to write data from a data source in the data flow to the Cache connection manager.</span></span>  
  
    -   <span data-ttu-id="d936c-120">从缓存文件读取数据。</span><span class="sxs-lookup"><span data-stu-id="d936c-120">Read data from the cache file.</span></span>  
  
     <span data-ttu-id="d936c-121">有关详细信息，请参阅 [Cache Transform](../data-flow/transformations/cache-transform.md)。</span><span class="sxs-lookup"><span data-stu-id="d936c-121">For more information, see [Cache Transform](../data-flow/transformations/cache-transform.md).</span></span>  
  
-   <span data-ttu-id="d936c-122">更改缓存中存储的列的元数据。</span><span class="sxs-lookup"><span data-stu-id="d936c-122">Change metadata for the columns stored in the cache.</span></span>  
  
-   <span data-ttu-id="d936c-123">使用表达式在运行时更新缓存文件名，以设置 ConnectionString 属性。</span><span class="sxs-lookup"><span data-stu-id="d936c-123">Update the cache file name at runtime by using an expression to set the ConnectionString property.</span></span> <span data-ttu-id="d936c-124">有关详细信息，请参阅 [在包中使用属性表达式](../expressions/use-property-expressions-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="d936c-124">For more information, see [Use Property Expressions in Packages](../expressions/use-property-expressions-in-packages.md).</span></span>  
  
 <span data-ttu-id="d936c-125">可以通过 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="d936c-125">You can set properties through [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="d936c-126">有关可以在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 设计器中设置的属性的详细信息，请参阅 [缓存连接管理器编辑器](../cache-connection-manager-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="d936c-126">For more information about the properties that you can set in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Designer, see [Cache Connection Manager Editor](../cache-connection-manager-editor.md).</span></span>  
  
 <span data-ttu-id="d936c-127">有关如何以编程方式配置连接管理器的信息，请参阅 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 和[以编程方式添加连接](../building-packages-programmatically/adding-connections-programmatically.md)。</span><span class="sxs-lookup"><span data-stu-id="d936c-127">For information about how to configure a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="d936c-128">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="d936c-128">Related Tasks</span></span>  
 [<span data-ttu-id="d936c-129">在完全缓存模式下使用缓存连接管理器实现查找转换</span><span class="sxs-lookup"><span data-stu-id="d936c-129">Implement a Lookup Transformation in Full Cache Mode Using the Cache Connection Manager</span></span>](lookup-transformation-full-cache-mode-ole-db-connection-manager.md)  
  
  
