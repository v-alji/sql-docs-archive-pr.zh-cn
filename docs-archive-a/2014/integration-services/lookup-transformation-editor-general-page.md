---
title: 查找转换编辑器 (常规页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.lookuptransformation.general.f1
ms.assetid: 4bd15e48-0feb-4f95-be91-5df58105dbfb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: aa178118f7e090b6a3c15c7ab9347f322461f07b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688024"
---
# <a name="lookup-transformation-editor-general-page"></a><span data-ttu-id="7e0c5-102">查找转换编辑器（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="7e0c5-102">Lookup Transformation Editor (General Page)</span></span>
  <span data-ttu-id="7e0c5-103">可以使用“查找转换编辑器”对话框的 **“常规”** 页，选择缓存模式，选择连接类型以及指定如何处理没有匹配项的行。</span><span class="sxs-lookup"><span data-stu-id="7e0c5-103">Use the **General** page of the Lookup Transformation Editor dialog box to select the cache mode, select the connection type, and specify how to handle rows with no matching entries.</span></span>  
  
 <span data-ttu-id="7e0c5-104">若要了解有关查找转换的详细信息，请参阅 [Lookup Transformation](data-flow/transformations/lookup-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="7e0c5-104">To learn more about the Lookup transformation, see [Lookup Transformation](data-flow/transformations/lookup-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="7e0c5-105">选项</span><span class="sxs-lookup"><span data-stu-id="7e0c5-105">Options</span></span>  
 <span data-ttu-id="7e0c5-106">**完全缓存**</span><span class="sxs-lookup"><span data-stu-id="7e0c5-106">**Full cache**</span></span>  
 <span data-ttu-id="7e0c5-107">在执行查找转换前，生成引用数据集并将其加载到缓存中。</span><span class="sxs-lookup"><span data-stu-id="7e0c5-107">Generate and load the reference dataset into cache before the Lookup transformation is executed.</span></span>  
  
 <span data-ttu-id="7e0c5-108">**部分缓存**</span><span class="sxs-lookup"><span data-stu-id="7e0c5-108">**Partial cache**</span></span>  
 <span data-ttu-id="7e0c5-109">在执行查找转换的过程中生成引用数据集。</span><span class="sxs-lookup"><span data-stu-id="7e0c5-109">Generate the reference dataset during the execution of the Lookup transformation.</span></span> <span data-ttu-id="7e0c5-110">将在引用数据集内有匹配项的行加载到缓存中，并将数据集内没有匹配项的行加载到缓存中。</span><span class="sxs-lookup"><span data-stu-id="7e0c5-110">Load the rows with matching entries in the reference dataset and the rows with no matching entries in the dataset into cache.</span></span>  
  
 <span data-ttu-id="7e0c5-111">**无缓存**</span><span class="sxs-lookup"><span data-stu-id="7e0c5-111">**No cache**</span></span>  
 <span data-ttu-id="7e0c5-112">在执行查找转换的过程中生成引用数据集。</span><span class="sxs-lookup"><span data-stu-id="7e0c5-112">Generate the reference dataset during the execution of the Lookup transformation.</span></span> <span data-ttu-id="7e0c5-113">不向缓存中加载任何数据。</span><span class="sxs-lookup"><span data-stu-id="7e0c5-113">No data is loaded into cache.</span></span>  
  
 <span data-ttu-id="7e0c5-114">**缓存连接管理器**</span><span class="sxs-lookup"><span data-stu-id="7e0c5-114">**Cache connection manager**</span></span>  
 <span data-ttu-id="7e0c5-115">将查找转换功能配置为使用缓存连接管理器。</span><span class="sxs-lookup"><span data-stu-id="7e0c5-115">Configure the Lookup transformation to use a Cache connection manager.</span></span> <span data-ttu-id="7e0c5-116">只有当选择了“完全缓存”选项时，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="7e0c5-116">This option is available only if the Full cache option is selected.</span></span>  
  
 <span data-ttu-id="7e0c5-117">**“无缓存”**</span><span class="sxs-lookup"><span data-stu-id="7e0c5-117">**OLE DB connection manager**</span></span>  
 <span data-ttu-id="7e0c5-118">将查找转换功能配置为使用 OLE DB 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="7e0c5-118">Configure the Lookup transformation to use an OLE DB connection manager.</span></span>  
  
 <span data-ttu-id="7e0c5-119">**指定如何处理无匹配项的行**</span><span class="sxs-lookup"><span data-stu-id="7e0c5-119">**Specify how to handle rows with no matching entries**</span></span>  
 <span data-ttu-id="7e0c5-120">选择一个选项来处理在引用数据集内没有任何匹配项的行。</span><span class="sxs-lookup"><span data-stu-id="7e0c5-120">Select an option for handling rows that do not match at least one entry in the reference dataset.</span></span>  
  
 <span data-ttu-id="7e0c5-121">如果选中 **“将行重定向到无匹配输出”**，则行将重定向到无匹配输出，并且将不作为错误处理。</span><span class="sxs-lookup"><span data-stu-id="7e0c5-121">When you select **Redirect rows to no match output**, the rows are redirected to a no match output and are not handled as errors.</span></span> <span data-ttu-id="7e0c5-122">**“查找转换编辑器”** 对话框的 **“错误输出”** 页上的 **“错误”** 选项不可用。</span><span class="sxs-lookup"><span data-stu-id="7e0c5-122">The **Error** option on the **Error Output** page of the **Lookup Transformation Editor** dialog box is not available.</span></span>  
  
 <span data-ttu-id="7e0c5-123">如果选中 **“指定如何处理无匹配项的行”** 列表框中的任何其他选项，则行将作为错误处理。</span><span class="sxs-lookup"><span data-stu-id="7e0c5-123">When you select any other option in the **Specify how to handle rows with no matching entries** list box, the rows are handled as errors.</span></span> <span data-ttu-id="7e0c5-124">**“错误输出”** 页上的 **“错误”** 选项不可用。</span><span class="sxs-lookup"><span data-stu-id="7e0c5-124">The **Error** option on the **Error Output** page is available.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="7e0c5-125">外部资源</span><span class="sxs-lookup"><span data-stu-id="7e0c5-125">External Resources</span></span>  
 <span data-ttu-id="7e0c5-126">blogs.msdn.com 上的博客文章： [查找缓存模式](https://go.microsoft.com/fwlink/?LinkId=219518)</span><span class="sxs-lookup"><span data-stu-id="7e0c5-126">Blog entry, [Lookup cache modes](https://go.microsoft.com/fwlink/?LinkId=219518) on blogs.msdn.com</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e0c5-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7e0c5-127">See Also</span></span>  
 <span data-ttu-id="7e0c5-128">[缓存连接管理器](connection-manager/cache-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="7e0c5-128">[Cache Connection Manager](connection-manager/cache-connection-manager.md) </span></span>  
 <span data-ttu-id="7e0c5-129">[查找转换编辑器 &#40;连接页&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md) </span><span class="sxs-lookup"><span data-stu-id="7e0c5-129">[Lookup Transformation Editor &#40;Connection Page&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md) </span></span>  
 <span data-ttu-id="7e0c5-130">[查找转换编辑器 &#40;列 "页&#41;](../../2014/integration-services/lookup-transformation-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="7e0c5-130">[Lookup Transformation Editor &#40;Columns Page&#41;](../../2014/integration-services/lookup-transformation-editor-columns-page.md) </span></span>  
 <span data-ttu-id="7e0c5-131">[查找转换编辑器 &#40;高级页面&#41;](../../2014/integration-services/lookup-transformation-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="7e0c5-131">[Lookup Transformation Editor &#40;Advanced Page&#41;](../../2014/integration-services/lookup-transformation-editor-advanced-page.md) </span></span>  
 [<span data-ttu-id="7e0c5-132">查找转换编辑器（“错误输出”页）</span><span class="sxs-lookup"><span data-stu-id="7e0c5-132">Lookup Transformation Editor &#40;Error Output Page&#41;</span></span>](../../2014/integration-services/lookup-transformation-editor-error-output-page.md)  
  
  
