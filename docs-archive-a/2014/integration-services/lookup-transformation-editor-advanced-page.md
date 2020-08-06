---
title: 查找转换编辑器 (高级页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.lookuptransformation.advanced.f1
helpviewer_keywords:
- Lookup Transformation Editor
ms.assetid: f3395c65-0320-47f9-8d83-daaa082d8713
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 23f235ef0506da7ac808d832db6ac36d53cfa604
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586804"
---
# <a name="lookup-transformation-editor-advanced-page"></a><span data-ttu-id="bf855-102">查找转换编辑器（“高级”页）</span><span class="sxs-lookup"><span data-stu-id="bf855-102">Lookup Transformation Editor (Advanced Page)</span></span>
  <span data-ttu-id="bf855-103">可以使用 **“查找转换编辑器”** 对话框的 **“高级”** 页，配置部分缓存以及修改查找转换的 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="bf855-103">Use the **Advanced** page of the **Lookup Transformation Editor** dialog box to configure partial caching and to modify the SQL statement for the Lookup transformation.</span></span>  
  
 <span data-ttu-id="bf855-104">若要了解有关查找转换的详细信息，请参阅 [Lookup Transformation](data-flow/transformations/lookup-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="bf855-104">To learn more about the Lookup transformation, see [Lookup Transformation](data-flow/transformations/lookup-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="bf855-105">选项</span><span class="sxs-lookup"><span data-stu-id="bf855-105">Options</span></span>  
 <span data-ttu-id="bf855-106">**缓存大小(32 位)**</span><span class="sxs-lookup"><span data-stu-id="bf855-106">**Cache size (32-bit)**</span></span>  
 <span data-ttu-id="bf855-107">调整 32 位计算机的缓存大小 (MB)。</span><span class="sxs-lookup"><span data-stu-id="bf855-107">Adjust the  cache size (in megabytes) for 32-bit computers.</span></span> <span data-ttu-id="bf855-108">默认值为 5 MB。</span><span class="sxs-lookup"><span data-stu-id="bf855-108">The default value is 5 megabytes.</span></span>  
  
 <span data-ttu-id="bf855-109">**缓存大小(64 位)**</span><span class="sxs-lookup"><span data-stu-id="bf855-109">**Cache size (64-bit)**</span></span>  
 <span data-ttu-id="bf855-110">调整 64 位计算机的缓存大小 (MB)。</span><span class="sxs-lookup"><span data-stu-id="bf855-110">Adjust the cache size (in megabytes) for 64-bit computers.</span></span> <span data-ttu-id="bf855-111">默认值为 5 MB。</span><span class="sxs-lookup"><span data-stu-id="bf855-111">The default value is 5 megabytes.</span></span>  
  
 <span data-ttu-id="bf855-112">**为无匹配项的行启用缓存**</span><span class="sxs-lookup"><span data-stu-id="bf855-112">**Enable cache for rows with no matching entries**</span></span>  
 <span data-ttu-id="bf855-113">缓存在引用数据集内没有匹配项的行。</span><span class="sxs-lookup"><span data-stu-id="bf855-113">Cache rows with no matching entries in the reference dataset.</span></span>  
  
 <span data-ttu-id="bf855-114">**缓存的分配额**</span><span class="sxs-lookup"><span data-stu-id="bf855-114">**Allocation from cache**</span></span>  
 <span data-ttu-id="bf855-115">指定要针对在引用数据集内没有匹配项的行分配的缓存所占的百分比。</span><span class="sxs-lookup"><span data-stu-id="bf855-115">Specify the percentage of the cache to allocate for rows with no matching entries in the reference dataset.</span></span>  
  
 <span data-ttu-id="bf855-116">**修改 SQL 语句**</span><span class="sxs-lookup"><span data-stu-id="bf855-116">**Modify the SQL statement**</span></span>  
 <span data-ttu-id="bf855-117">修改用来生成引用数据集的 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="bf855-117">Modify the SQL statement that is used to generate the reference dataset.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bf855-118">在此页上指定的可选 SQL 语句将覆盖并替换在 **“查找转换编辑器”** 的 **“高级”** 页上指定的表名。</span><span class="sxs-lookup"><span data-stu-id="bf855-118">The optional SQL statement that you specify on this page overrides and replaces the table name that you specified on the **Connection** page of the **Lookup Transformation Editor**.</span></span> <span data-ttu-id="bf855-119">有关详细信息，请参阅 [查找转换编辑器（“连接”页）](../../2014/integration-services/lookup-transformation-editor-connection-page.md)。</span><span class="sxs-lookup"><span data-stu-id="bf855-119">For more information, see [Lookup Transformation Editor &#40;Connection Page&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md).</span></span>  
  
 <span data-ttu-id="bf855-120">**设置参数**</span><span class="sxs-lookup"><span data-stu-id="bf855-120">**Set Parameters**</span></span>  
 <span data-ttu-id="bf855-121">使用“设置查询参数”\*\*\*\* 对话框将输入列映射到参数。</span><span class="sxs-lookup"><span data-stu-id="bf855-121">Map input columns to parameters by using the **Set Query Parameters** dialog box.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="bf855-122">外部资源</span><span class="sxs-lookup"><span data-stu-id="bf855-122">External Resources</span></span>  
 <span data-ttu-id="bf855-123">blogs.msdn.com 上的博客文章： [查找缓存模式](https://go.microsoft.com/fwlink/?LinkId=219518)</span><span class="sxs-lookup"><span data-stu-id="bf855-123">Blog entry, [Lookup cache modes](https://go.microsoft.com/fwlink/?LinkId=219518) on blogs.msdn.com</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf855-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bf855-124">See Also</span></span>  
 <span data-ttu-id="bf855-125">[查找转换编辑器 &#40;常规页&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="bf855-125">[Lookup Transformation Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="bf855-126">[查找转换编辑器 &#40;连接页&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md) </span><span class="sxs-lookup"><span data-stu-id="bf855-126">[Lookup Transformation Editor &#40;Connection Page&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md) </span></span>  
 <span data-ttu-id="bf855-127">[查找转换编辑器 &#40;列 "页&#41;](../../2014/integration-services/lookup-transformation-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="bf855-127">[Lookup Transformation Editor &#40;Columns Page&#41;](../../2014/integration-services/lookup-transformation-editor-columns-page.md) </span></span>  
 <span data-ttu-id="bf855-128">[查找转换编辑器 &#40;错误输出页&#41;](../../2014/integration-services/lookup-transformation-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="bf855-128">[Lookup Transformation Editor &#40;Error Output Page&#41;](../../2014/integration-services/lookup-transformation-editor-error-output-page.md) </span></span>  
 <span data-ttu-id="bf855-129">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="bf855-129">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="bf855-130">模糊查找转换</span><span class="sxs-lookup"><span data-stu-id="bf855-130">Fuzzy Lookup Transformation</span></span>](data-flow/transformations/fuzzy-lookup-transformation.md)  
  
  
