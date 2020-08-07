---
title: OData 源编辑器 (连接页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- Sql12.dts.designer.odatasource.connection.f1
ms.assetid: 20bcd347-4547-4fad-b182-9571030101df
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6ecd0d060ea2197ae7174325b654645fefa23505
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587900"
---
# <a name="odata-source-editor-connection-page"></a><span data-ttu-id="e4254-102">OData 源编辑器（“连接”页）</span><span class="sxs-lookup"><span data-stu-id="e4254-102">OData Source Editor (Connection Page)</span></span>
  <span data-ttu-id="e4254-103">可以使用 **“OData 源编辑器”** 对话框的 **“连接”** 页，为 OData 源选择 OData 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="e4254-103">Use the **Connection** page of the **OData Source Editor** dialog box to select the OData connection manager for the OData source.</span></span> <span data-ttu-id="e4254-104">通过此页还可以指定集合或资源路径和任何查询选项以指示需要从 OData 源检索的数据。</span><span class="sxs-lookup"><span data-stu-id="e4254-104">This page also lets you specify a collection or a resource path and any query options to indicate what data needs to be retrieved from the OData source.</span></span> <span data-ttu-id="e4254-105">若要了解有关 OData 源的详细信息，请参阅 [OData Source](data-flow/odata-source.md)。</span><span class="sxs-lookup"><span data-stu-id="e4254-105">To learn more about the OData source, see [OData Source](data-flow/odata-source.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="e4254-106">静态选项</span><span class="sxs-lookup"><span data-stu-id="e4254-106">Static Options</span></span>  
 <span data-ttu-id="e4254-107">**OData 连接管理器**</span><span class="sxs-lookup"><span data-stu-id="e4254-107">**OData connection manager**</span></span>  
 <span data-ttu-id="e4254-108">从列表中选择一个现有连接管理器，或通过单击“新建”  创建一个新连接。</span><span class="sxs-lookup"><span data-stu-id="e4254-108">Select an existing connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="e4254-109">**新建**</span><span class="sxs-lookup"><span data-stu-id="e4254-109">**New**</span></span>  
 <span data-ttu-id="e4254-110">通过使用“OData 连接管理器编辑器”\*\*\*\* 对话框创建新的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="e4254-110">Create a new connection manager by using the **OData Connection Manager Editor** dialog box.</span></span>  
  
 <span data-ttu-id="e4254-111">**使用集合或资源路径**</span><span class="sxs-lookup"><span data-stu-id="e4254-111">**Use collection or resource path**</span></span>  
 <span data-ttu-id="e4254-112">指定从源选择数据的方法。</span><span class="sxs-lookup"><span data-stu-id="e4254-112">Specify the method for selecting data from the source.</span></span>  
  
|<span data-ttu-id="e4254-113">选项</span><span class="sxs-lookup"><span data-stu-id="e4254-113">Option</span></span>|<span data-ttu-id="e4254-114">说明</span><span class="sxs-lookup"><span data-stu-id="e4254-114">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="e4254-115">集合</span><span class="sxs-lookup"><span data-stu-id="e4254-115">Collection</span></span>|<span data-ttu-id="e4254-116">使用集合名称查询从 OData 源检索数据。</span><span class="sxs-lookup"><span data-stu-id="e4254-116">Retrieve data from the OData source by using a collection name.</span></span>|  
|<span data-ttu-id="e4254-117">资源路径</span><span class="sxs-lookup"><span data-stu-id="e4254-117">Resource Path</span></span>|<span data-ttu-id="e4254-118">使用资源路径查询从 OData 源检索数据。</span><span class="sxs-lookup"><span data-stu-id="e4254-118">Retrieve data from the OData source by using a resource path.</span></span>|  
  
 <span data-ttu-id="e4254-119">**查询选项**</span><span class="sxs-lookup"><span data-stu-id="e4254-119">**Query options**</span></span>  
 <span data-ttu-id="e4254-120">为查询指定选项。</span><span class="sxs-lookup"><span data-stu-id="e4254-120">Specify options for the query.</span></span>  <span data-ttu-id="e4254-121">例如：$top=5。</span><span class="sxs-lookup"><span data-stu-id="e4254-121">For example: $top=5</span></span>  
  
 <span data-ttu-id="e4254-122">**馈送 url**</span><span class="sxs-lookup"><span data-stu-id="e4254-122">**Feed url**</span></span>  
 <span data-ttu-id="e4254-123">基于在此对话框中选择的选项显示只读馈送 URL。</span><span class="sxs-lookup"><span data-stu-id="e4254-123">Displays the read-only Feed URL based on options you selected on this dialog box.</span></span>  
  
 <span data-ttu-id="e4254-124">**预览**</span><span class="sxs-lookup"><span data-stu-id="e4254-124">**Preview**</span></span>  
 <span data-ttu-id="e4254-125">通过使用“预览”\*\*\*\* 对话框预览结果。</span><span class="sxs-lookup"><span data-stu-id="e4254-125">Preview results by using the **Preview** dialog box.</span></span> <span data-ttu-id="e4254-126">**“预览”** 最多可以显示 20 行。</span><span class="sxs-lookup"><span data-stu-id="e4254-126">**Preview** can display up to 20 rows.</span></span>  
  
## <a name="dynamic-options"></a><span data-ttu-id="e4254-127">动态选项</span><span class="sxs-lookup"><span data-stu-id="e4254-127">Dynamic Options</span></span>  
  
### <a name="use-collection-or-resource-path--collection"></a><span data-ttu-id="e4254-128">使用集合或资源路径 = 集合</span><span class="sxs-lookup"><span data-stu-id="e4254-128">Use collection or resource path = Collection</span></span>  
 <span data-ttu-id="e4254-129">**集合**</span><span class="sxs-lookup"><span data-stu-id="e4254-129">**Collection**</span></span>  
 <span data-ttu-id="e4254-130">从下拉列表中选择集合。</span><span class="sxs-lookup"><span data-stu-id="e4254-130">Select a collection from the drop-down list.</span></span>  
  
### <a name="use-collection-or-resource-path--resource-path"></a><span data-ttu-id="e4254-131">使用集合或资源路径 = 资源路径</span><span class="sxs-lookup"><span data-stu-id="e4254-131">Use collection or resource path = Resource Path</span></span>  
 <span data-ttu-id="e4254-132">**资源路径**</span><span class="sxs-lookup"><span data-stu-id="e4254-132">**Resource path**</span></span>  
 <span data-ttu-id="e4254-133">键入资源路径。</span><span class="sxs-lookup"><span data-stu-id="e4254-133">Type a resource path.</span></span> <span data-ttu-id="e4254-134">例如：Employees</span><span class="sxs-lookup"><span data-stu-id="e4254-134">For example: Employees</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4254-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e4254-135">See Also</span></span>  
 <span data-ttu-id="e4254-136">[OData 源编辑器 &#40;列 "页&#41;](../../2014/integration-services/odata-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="e4254-136">[OData Source Editor &#40;Columns Page&#41;](../../2014/integration-services/odata-source-editor-columns-page.md) </span></span>  
 <span data-ttu-id="e4254-137">[OData 源编辑器 &#40;错误输出页&#41;](../../2014/integration-services/odata-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="e4254-137">[OData Source Editor &#40;Error Output Page&#41;](../../2014/integration-services/odata-source-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="e4254-138">OData 连接管理器</span><span class="sxs-lookup"><span data-stu-id="e4254-138">OData Connection Manager</span></span>](connection-manager/odata-connection-manager.md)  
  
  
