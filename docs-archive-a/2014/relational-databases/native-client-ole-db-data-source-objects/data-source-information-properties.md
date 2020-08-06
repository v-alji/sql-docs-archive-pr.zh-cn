---
title: 数据源信息属性 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, data source properties
- properties [OLE DB]
- data source properties [OLE DB]
- information properties [OLE DB]
- OLE DB data source properties [SQL Server Native Client]
ms.assetid: 7fd80e47-5bd9-41e2-a3d3-091a7c8c5f2b
author: rothja
ms.author: jroth
ms.openlocfilehash: c10a4e762bbe3421e720753941f5e0a5702832ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693277"
---
# <a name="data-source-information-properties"></a><span data-ttu-id="abaa5-102">数据源信息属性</span><span class="sxs-lookup"><span data-stu-id="abaa5-102">Data Source Information Properties</span></span>
  <span data-ttu-id="abaa5-103">在特定于访问接口的属性集 DBPROPSET_SQLSERVERDATASOURCEINFO 中，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 访问接口定义了以下数据源信息属性。</span><span class="sxs-lookup"><span data-stu-id="abaa5-103">In the provider-specific property set DBPROPSET_SQLSERVERDATASOURCEINFO, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider defines the following data source information properties.</span></span>  
  
|<span data-ttu-id="abaa5-104">属性 ID</span><span class="sxs-lookup"><span data-stu-id="abaa5-104">Property ID</span></span>|<span data-ttu-id="abaa5-105">说明</span><span class="sxs-lookup"><span data-stu-id="abaa5-105">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="abaa5-106">SSPROP_COLUMNLEVELCOLLATION</span><span class="sxs-lookup"><span data-stu-id="abaa5-106">SSPROP_COLUMNLEVELCOLLATION</span></span>|<span data-ttu-id="abaa5-107">键入：VT_BOOL</span><span class="sxs-lookup"><span data-stu-id="abaa5-107">Type: VT_BOOL</span></span><br /><br /> <span data-ttu-id="abaa5-108">读取/写入：读取</span><span class="sxs-lookup"><span data-stu-id="abaa5-108">R/W: Read</span></span><br /><br /> <span data-ttu-id="abaa5-109">默认值：VARIANT_TRUE</span><span class="sxs-lookup"><span data-stu-id="abaa5-109">Default: VARIANT_TRUE</span></span><br /><br /> <span data-ttu-id="abaa5-110">说明：用于确定是否支持列排序规则。</span><span class="sxs-lookup"><span data-stu-id="abaa5-110">Description: Used to determine if column collation is supported.</span></span><br /><br /> <span data-ttu-id="abaa5-111">VARIANT_TRUE：支持列级别排序规则。</span><span class="sxs-lookup"><span data-stu-id="abaa5-111">VARIANT_TRUE: Column level collation is supported.</span></span><br /><br /> <span data-ttu-id="abaa5-112">VARIANT_FALSE：不支持列级别排序规则。</span><span class="sxs-lookup"><span data-stu-id="abaa5-112">VARIANT_FALSE: Column level collation is not supported.</span></span>|  
|<span data-ttu-id="abaa5-113">SSPROP_UNICODELCID</span><span class="sxs-lookup"><span data-stu-id="abaa5-113">SSPROP_UNICODELCID</span></span>|<span data-ttu-id="abaa5-114">类型：VT_I4 读取/写入：读取</span><span class="sxs-lookup"><span data-stu-id="abaa5-114">Type: VT_I4 R/W: Read</span></span><br /><br /> <span data-ttu-id="abaa5-115">说明：Unicode 区域设置 ID。</span><span class="sxs-lookup"><span data-stu-id="abaa5-115">Description: Unicode locale ID.</span></span><br /><br /> <span data-ttu-id="abaa5-116">这是用于 Unicode 数据排序的区域设置。</span><span class="sxs-lookup"><span data-stu-id="abaa5-116">This is the locale used for Unicode data sorting.</span></span>|  
|<span data-ttu-id="abaa5-117">SSPROP_UNICODECOMPARISONSTYLE</span><span class="sxs-lookup"><span data-stu-id="abaa5-117">SSPROP_UNICODECOMPARISONSTYLE</span></span>|<span data-ttu-id="abaa5-118">类型：VT_I4 读取/写入：读取</span><span class="sxs-lookup"><span data-stu-id="abaa5-118">Type: VT_I4 R/W: Read</span></span><br /><br /> <span data-ttu-id="abaa5-119">说明：Unicode 比较样式。</span><span class="sxs-lookup"><span data-stu-id="abaa5-119">Description: Unicode comparison style.</span></span><br /><br /> <span data-ttu-id="abaa5-120">用于 Unicode 数据排序的排序选项。</span><span class="sxs-lookup"><span data-stu-id="abaa5-120">The sorting options used for Unicode data sorting.</span></span>|  
  
 <span data-ttu-id="abaa5-121">在特定于访问接口的属性集 DBPROPSET_SQLSERVERSTREAM 中，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 访问接口定义了以下附加属性。</span><span class="sxs-lookup"><span data-stu-id="abaa5-121">In the provider-specific property set DBPROPSET_SQLSERVERSTREAM, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider defines the following additional property.</span></span>  
  
|<span data-ttu-id="abaa5-122">属性 ID</span><span class="sxs-lookup"><span data-stu-id="abaa5-122">Property ID</span></span>|<span data-ttu-id="abaa5-123">说明</span><span class="sxs-lookup"><span data-stu-id="abaa5-123">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="abaa5-124">SSPROP_STREAM_XMLROOT</span><span class="sxs-lookup"><span data-stu-id="abaa5-124">SSPROP_STREAM_XMLROOT</span></span>|<span data-ttu-id="abaa5-125">类型：VT_BSTR 读取/写入：读取/写入</span><span class="sxs-lookup"><span data-stu-id="abaa5-125">Type: VT_BSTR R/W: Read/Write</span></span><br /><br /> <span data-ttu-id="abaa5-126">说明：FOR XML 查询的结果可能不是格式正确的文档。</span><span class="sxs-lookup"><span data-stu-id="abaa5-126">Description: The result of a FOR XML query may not be a well-formed document.</span></span> <span data-ttu-id="abaa5-127">如果此属性已指定，“select ... for XML”查询结果会被包装在此属性提供的根标记中，以返回格式正确的 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="abaa5-127">When this property is specified, the result of a 'select ... for XML' query is wrapped in the root tag provided by this property to return a well formed XML document.</span></span> <span data-ttu-id="abaa5-128">如果查询是在浏览器中执行的，在加载结果时它可能导致浏览器显示分析器错误。</span><span class="sxs-lookup"><span data-stu-id="abaa5-128">If the query is executed in the browser it may cause the browser to display parser errors when loading the result.</span></span> <span data-ttu-id="abaa5-129">为了避免错误，SQL ISAPI 支持 ROOT 关键字。</span><span class="sxs-lookup"><span data-stu-id="abaa5-129">To avoid the error, SQL ISAPI supports the keyword ROOT.</span></span> <span data-ttu-id="abaa5-130">此关键字映射到 SSPROP_STREAM_XMLROOT 属性。</span><span class="sxs-lookup"><span data-stu-id="abaa5-130">This keyword maps to SSPROP_STREAM_XMLROOT property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="abaa5-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="abaa5-131">See Also</span></span>  
 [<span data-ttu-id="abaa5-132">数据源对象 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="abaa5-132">Data Source Objects &#40;OLE DB&#41;</span></span>](data-source-objects-ole-db.md)  
  
  
