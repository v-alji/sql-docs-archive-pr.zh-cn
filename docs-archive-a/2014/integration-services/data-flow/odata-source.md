---
title: OData 源 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.ODATASOURCE.F1
ms.assetid: cc9003c9-638e-432b-867e-e949d50cec90
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 98b14ef034597f6098f70386ca41c1b90be86500
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693407"
---
# <a name="odata-source"></a><span data-ttu-id="1afad-102">OData 源</span><span class="sxs-lookup"><span data-stu-id="1afad-102">OData Source</span></span>
  <span data-ttu-id="1afad-103">可在 SSIS 包中使用 OData 源组件，以使用来自开放式数据协议 (OData) 服务的数据。</span><span class="sxs-lookup"><span data-stu-id="1afad-103">You use the OData Source component in an SSIS package to consume data from Open Data Protocol (OData) services.</span></span> <span data-ttu-id="1afad-104">该组件支持 OData v2 和 v3 协议以及 ATOM 和 JSON 数据格式。</span><span class="sxs-lookup"><span data-stu-id="1afad-104">The component supports the OData v2 and v3 protocols, as well as the ATOM and JSON data formats.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1afad-105">OData 源可用于从 SharePoint 列表读取。</span><span class="sxs-lookup"><span data-stu-id="1afad-105">The OData Source can be used to read from SharePoint lists.</span></span> <span data-ttu-id="1afad-106">若要查看 SharePoint 服务器上的所有列表，请使用以下 URL： http:// \<server> /_vti_bin/listdata.svc。</span><span class="sxs-lookup"><span data-stu-id="1afad-106">To see all lists on your SharePoint server, use the following URL: http://\<server>/_vti_bin/ListData.svc.</span></span> <span data-ttu-id="1afad-107">有关 SharePoint URL 约定的详细信息，请参阅 [SharePoint Foundation REST 接口](https://msdn.microsoft.com/library/ff521587.aspx)。</span><span class="sxs-lookup"><span data-stu-id="1afad-107">For more information about SharePoint URL conventions, see [SharePoint Foundation REST Interface](https://msdn.microsoft.com/library/ff521587.aspx).</span></span>  
  
## <a name="odata-format"></a><span data-ttu-id="1afad-108">OData 格式</span><span class="sxs-lookup"><span data-stu-id="1afad-108">OData Format</span></span>  
 <span data-ttu-id="1afad-109">大多数 OData 服务采用多种格式返回结果。</span><span class="sxs-lookup"><span data-stu-id="1afad-109">Most OData services return results in multiple formats.</span></span> <span data-ttu-id="1afad-110">可以使用 $format 查询选项指定结果集的格式。</span><span class="sxs-lookup"><span data-stu-id="1afad-110">You can specify the format of the result set by using the $format query option.</span></span> <span data-ttu-id="1afad-111">传输大量数据时，JSON 和 JSON 轻型这类格式比 ATOM/XML 更高效，可以提供更佳性能。</span><span class="sxs-lookup"><span data-stu-id="1afad-111">Formats such as JSON and JSON Light are more efficient than ATOM/XML, and may give you better performance when transferring large amounts of data.</span></span> <span data-ttu-id="1afad-112">下表提供来自示例测试的结果。</span><span class="sxs-lookup"><span data-stu-id="1afad-112">The following table provides results from sample tests.</span></span> <span data-ttu-id="1afad-113">可以看到，从 ATOM 切换为 JSON 时，性能提高 30-53%，从 ATOM 切换为新的 JSON 轻型格式（WCF Data Services 5.1 中提供）时，性能提高 67%。</span><span class="sxs-lookup"><span data-stu-id="1afad-113">As you can see, there was a 30-53% performance gain when switching from ATOM to JSON and 67% performance gain when switching from ATOM to the new JSON light format (available in WCF Data Services 5.1).</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="1afad-114">“行”</span><span class="sxs-lookup"><span data-stu-id="1afad-114">Rows</span></span>|<span data-ttu-id="1afad-115">ATOM</span><span class="sxs-lookup"><span data-stu-id="1afad-115">ATOM</span></span>|<span data-ttu-id="1afad-116">JSON</span><span class="sxs-lookup"><span data-stu-id="1afad-116">JSON</span></span>|<span data-ttu-id="1afad-117">JSON（轻型）</span><span class="sxs-lookup"><span data-stu-id="1afad-117">JSON (Light)</span></span>|  
|<span data-ttu-id="1afad-118">10000</span><span class="sxs-lookup"><span data-stu-id="1afad-118">10000</span></span>|<span data-ttu-id="1afad-119">113 秒</span><span class="sxs-lookup"><span data-stu-id="1afad-119">113 seconds</span></span>|<span data-ttu-id="1afad-120">74 秒</span><span class="sxs-lookup"><span data-stu-id="1afad-120">74 seconds</span></span>|<span data-ttu-id="1afad-121">68 秒</span><span class="sxs-lookup"><span data-stu-id="1afad-121">68 seconds</span></span>|  
|<span data-ttu-id="1afad-122">1000000</span><span class="sxs-lookup"><span data-stu-id="1afad-122">1000000</span></span>|<span data-ttu-id="1afad-123">1110 秒</span><span class="sxs-lookup"><span data-stu-id="1afad-123">1110 seconds</span></span>|<span data-ttu-id="1afad-124">853 秒</span><span class="sxs-lookup"><span data-stu-id="1afad-124">853 seconds</span></span>|<span data-ttu-id="1afad-125">665 秒</span><span class="sxs-lookup"><span data-stu-id="1afad-125">665 seconds</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="1afad-126">SSIS OData 源使用 ODataLib 5.5.0 分析 OData 馈送，可以读取此库支持的所有格式。</span><span class="sxs-lookup"><span data-stu-id="1afad-126">The SSIS OData Source uses ODataLib 5.5.0 to parse OData feeds and it can read all formats supported by this library.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1afad-127">本节内容</span><span class="sxs-lookup"><span data-stu-id="1afad-127">In This Section</span></span>  
  
-   [<span data-ttu-id="1afad-128">安装和卸载 OData 源组件</span><span class="sxs-lookup"><span data-stu-id="1afad-128">Install and Uninstall OData Source Component</span></span>](../install-and-uninstall-odata-source-component.md)  
  
-   [<span data-ttu-id="1afad-129">教程：使用 OData 源 &#91;SSIS&#93;</span><span class="sxs-lookup"><span data-stu-id="1afad-129">Tutorial: Using the OData Source &#91;SSIS&#93;</span></span>](tutorial-using-the-odata-source.md)  
  
-   [<span data-ttu-id="1afad-130">在运行时修改 OData 源查询</span><span class="sxs-lookup"><span data-stu-id="1afad-130">Modify OData Source Query at Runtime</span></span>](modify-odata-source-query-at-runtime.md)  
  
-   [<span data-ttu-id="1afad-131">OData 源编辑器（“连接”页）</span><span class="sxs-lookup"><span data-stu-id="1afad-131">OData Source Editor &#40;Connection Page&#41;</span></span>](../odata-source-editor-connection-page.md)  
  
-   [<span data-ttu-id="1afad-132">OData 源编辑器（“列”页）</span><span class="sxs-lookup"><span data-stu-id="1afad-132">OData Source Editor &#40;Columns Page&#41;</span></span>](../odata-source-editor-columns-page.md)  
  
-   [<span data-ttu-id="1afad-133">OData 源编辑器（“错误输出”页）</span><span class="sxs-lookup"><span data-stu-id="1afad-133">OData Source Editor &#40;Error Output Page&#41;</span></span>](../odata-source-editor-error-output-page.md)  
  
-   [<span data-ttu-id="1afad-134">OData 源属性</span><span class="sxs-lookup"><span data-stu-id="1afad-134">OData Source Properties</span></span>](odata-source-properties.md)  
  
## <a name="see-also"></a><span data-ttu-id="1afad-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1afad-135">See Also</span></span>  
 [<span data-ttu-id="1afad-136">OData 连接管理器</span><span class="sxs-lookup"><span data-stu-id="1afad-136">OData Connection Manager</span></span>](../connection-manager/odata-connection-manager.md)  
  
  
