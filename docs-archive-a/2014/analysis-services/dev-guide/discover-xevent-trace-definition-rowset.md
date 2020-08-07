---
title: DISCOVER_XEVENT_TRACE_DEFINITION 行集 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: e1ce2d2d-f994-4318-801a-ee0385aecd84
author: minewiskan
ms.author: owend
ms.openlocfilehash: bedd6ec66a188738ac9a522b4802b3b431e82f36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690857"
---
# <a name="discover_xevent_trace_definition-rowset"></a><span data-ttu-id="73f98-102">DISCOVER_XEVENT_TRACE_DEFINITION 行集</span><span class="sxs-lookup"><span data-stu-id="73f98-102">DISCOVER_XEVENT_TRACE_DEFINITION Rowset</span></span>
  <span data-ttu-id="73f98-103">提供有关服务器上当前活动的 XEvent 跟踪的信息。</span><span class="sxs-lookup"><span data-stu-id="73f98-103">Provides information about XEvent traces that are currently active on the server.</span></span>  
  
 <span data-ttu-id="73f98-104">**适用于：** 表格模型和多维模型</span><span class="sxs-lookup"><span data-stu-id="73f98-104">**Applies to:** tabular models, multidimensional models</span></span>  
  
## <a name="rowset-columns"></a><span data-ttu-id="73f98-105">行集列</span><span class="sxs-lookup"><span data-stu-id="73f98-105">Rowset Columns</span></span>  
 <span data-ttu-id="73f98-106">`DISCOVER_XEVENT_TRACE_DEFINITION` 行集包含以下列。</span><span class="sxs-lookup"><span data-stu-id="73f98-106">The `DISCOVER_XEVENT_TRACE_DEFINITION` rowset contains the following columns.</span></span>  
  
|<span data-ttu-id="73f98-107">列名称</span><span class="sxs-lookup"><span data-stu-id="73f98-107">Column name</span></span>|<span data-ttu-id="73f98-108">类型指示符</span><span class="sxs-lookup"><span data-stu-id="73f98-108">Type indicator</span></span>|<span data-ttu-id="73f98-109">长度</span><span class="sxs-lookup"><span data-stu-id="73f98-109">Length</span></span>|<span data-ttu-id="73f98-110">说明</span><span class="sxs-lookup"><span data-stu-id="73f98-110">Description</span></span>|  
|-----------------|--------------------|------------|-----------------|  
|`Data`|`DBTYPE_WSTR`||<span data-ttu-id="73f98-111">XEvent 跟踪的 XML 定义。</span><span class="sxs-lookup"><span data-stu-id="73f98-111">The XML definition of the XEvent trace.</span></span>|  
  
 <span data-ttu-id="73f98-112">未对此架构行集进行排序。</span><span class="sxs-lookup"><span data-stu-id="73f98-112">This schema rowset is not sorted.</span></span>  
  
## <a name="using-adomdnet-to-return-the-rowset"></a><span data-ttu-id="73f98-113">使用 ADOMD.NET 返回行集</span><span class="sxs-lookup"><span data-stu-id="73f98-113">Using ADOMD.NET to return the rowset</span></span>  
 <span data-ttu-id="73f98-114">在使用 ADOMD.NET 和架构行集检索元数据时，可以使用 GUID 或字符串在 GetSchemaDataSet 方法中引用架构行集对象。</span><span class="sxs-lookup"><span data-stu-id="73f98-114">When using ADOMD.NET and the schema rowset to retrieve metadata, you can use either the GUID or string to reference a schema rowset object in the GetSchemaDataSet method.</span></span> <span data-ttu-id="73f98-115">有关详细信息，请参阅 [Working with Schema Rowsets in ADOMD.NET](https://docs.microsoft.com/bi-reference/adomd/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets)。</span><span class="sxs-lookup"><span data-stu-id="73f98-115">For more information, see [Working with Schema Rowsets in ADOMD.NET](https://docs.microsoft.com/bi-reference/adomd/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets).</span></span>  
  
 <span data-ttu-id="73f98-116">下表提供了用于标识此行集的 GUID 和字符串值。</span><span class="sxs-lookup"><span data-stu-id="73f98-116">The following table provides the GUID and string values that identify this rowset.</span></span>  
  
|<span data-ttu-id="73f98-117">参数</span><span class="sxs-lookup"><span data-stu-id="73f98-117">Argument</span></span>|<span data-ttu-id="73f98-118">值</span><span class="sxs-lookup"><span data-stu-id="73f98-118">Value</span></span>|  
|--------------|-----------|  
|<span data-ttu-id="73f98-119">GUID</span><span class="sxs-lookup"><span data-stu-id="73f98-119">GUID</span></span>|<span data-ttu-id="73f98-120">a07ccd1c-8148-11d0-87bb-00c04fc33942</span><span class="sxs-lookup"><span data-stu-id="73f98-120">a07ccd1c-8148-11d0-87bb-00c04fc33942</span></span>|  
|<span data-ttu-id="73f98-121">String</span><span class="sxs-lookup"><span data-stu-id="73f98-121">String</span></span>|<span data-ttu-id="73f98-122">DISCOVER_XEVENT_TRACE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="73f98-122">DISCOVER_XEVENT_TRACE_DEFINITION</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="73f98-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="73f98-123">See Also</span></span>  
 <span data-ttu-id="73f98-124">[XML for Analysis 架构行集](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/xml-for-analysis-schema-rowsets) </span><span class="sxs-lookup"><span data-stu-id="73f98-124">[XML for Analysis Schema Rowsets](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/xml-for-analysis-schema-rowsets) </span></span>  
 <span data-ttu-id="73f98-125">[使用 &#40;XEvents&#41; SQL Server 扩展事件监视 Analysis Services](../instances/monitor-analysis-services-with-sql-server-extended-events.md) </span><span class="sxs-lookup"><span data-stu-id="73f98-125">[Use SQL Server Extended Events &#40;XEvents&#41; to Monitor Analysis Services](../instances/monitor-analysis-services-with-sql-server-extended-events.md) </span></span>  
 [<span data-ttu-id="73f98-126">使用动态管理视图 (DMV) 监视 Analysis Services</span><span class="sxs-lookup"><span data-stu-id="73f98-126">Use Dynamic Management Views &#40;DMVs&#41; to Monitor Analysis Services</span></span>](../instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)  
  
  
