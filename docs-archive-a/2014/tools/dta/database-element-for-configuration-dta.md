---
title: 用于配置 (DTA) 的数据库元素 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Database element
ms.assetid: e91ba243-6cc9-457a-8f5a-134f3c71ae69
author: stevestein
ms.author: sstein
ms.openlocfilehash: 69ce1a0ac9912907f6d22916dd6243621e0778db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682537"
---
# <a name="database-element-for-configuration-dta"></a><span data-ttu-id="66a3f-102">用于配置的数据库元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="66a3f-102">Database Element for Configuration (DTA)</span></span>
  <span data-ttu-id="66a3f-103">指定要用数据库引擎优化顾问进行假设配置（由 `Configuration` 元素指定）评估的数据库。</span><span class="sxs-lookup"><span data-stu-id="66a3f-103">Specifies the database against which you want the Database Engine Tuning Advisor to evaluate the hypothetical configuration (specified by the `Configuration` element).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66a3f-104">语法</span><span class="sxs-lookup"><span data-stu-id="66a3f-104">Syntax</span></span>  
  
```  
  
<Server>  
...code removed here...  
    <Database>...</Database>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="66a3f-105">元素特征</span><span class="sxs-lookup"><span data-stu-id="66a3f-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="66a3f-106">特征</span><span class="sxs-lookup"><span data-stu-id="66a3f-106">Characteristic</span></span>|<span data-ttu-id="66a3f-107">说明</span><span class="sxs-lookup"><span data-stu-id="66a3f-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="66a3f-108">**数据类型和长度**</span><span class="sxs-lookup"><span data-stu-id="66a3f-108">**Data type and length**</span></span>|<span data-ttu-id="66a3f-109">无。</span><span class="sxs-lookup"><span data-stu-id="66a3f-109">None.</span></span>|  
|<span data-ttu-id="66a3f-110">**默认值**</span><span class="sxs-lookup"><span data-stu-id="66a3f-110">**Default value**</span></span>|<span data-ttu-id="66a3f-111">无。</span><span class="sxs-lookup"><span data-stu-id="66a3f-111">None.</span></span>|  
|<span data-ttu-id="66a3f-112">**出现次数**</span><span class="sxs-lookup"><span data-stu-id="66a3f-112">**Occurrence**</span></span>|<span data-ttu-id="66a3f-113">对于每个 `Server` 元素需要使用一次或多次。</span><span class="sxs-lookup"><span data-stu-id="66a3f-113">Required one or more times per `Server` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="66a3f-114">元素关系</span><span class="sxs-lookup"><span data-stu-id="66a3f-114">Element Relationships</span></span>  
  
|<span data-ttu-id="66a3f-115">关系</span><span class="sxs-lookup"><span data-stu-id="66a3f-115">Relationship</span></span>|<span data-ttu-id="66a3f-116">元素</span><span class="sxs-lookup"><span data-stu-id="66a3f-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="66a3f-117">**父元素**</span><span class="sxs-lookup"><span data-stu-id="66a3f-117">**Parent element**</span></span>|[<span data-ttu-id="66a3f-118">用于配置的服务器元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="66a3f-118">Server Element for Configuration &#40;DTA&#41;</span></span>](server-element-for-configuration-dta.md)|  
|<span data-ttu-id="66a3f-119">**子元素**</span><span class="sxs-lookup"><span data-stu-id="66a3f-119">**Child elements**</span></span>|[<span data-ttu-id="66a3f-120">数据库的名称元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="66a3f-120">Name Element for Database &#40;DTA&#41;</span></span>](name-element-for-database-dta.md)<br /><br /> [<span data-ttu-id="66a3f-121">数据库的架构元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="66a3f-121">Schema Element for Database &#40;DTA&#41;</span></span>](schema-element-for-database-dta.md)<br /><br /> [<span data-ttu-id="66a3f-122">建议元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="66a3f-122">Recommendation Element &#40;DTA&#41;</span></span>](recommendation-element-dta.md)|  
  
## <a name="remarks"></a><span data-ttu-id="66a3f-123">备注</span><span class="sxs-lookup"><span data-stu-id="66a3f-123">Remarks</span></span>  
 <span data-ttu-id="66a3f-124">在数据库引擎优化顾问 XML 架构中，此元素的名称为 **DatabaseTypecomplexType** 。</span><span class="sxs-lookup"><span data-stu-id="66a3f-124">This element is of the **DatabaseTypecomplexType** name in the Database Engine Tuning Advisor XML schema.</span></span> <span data-ttu-id="66a3f-125">不要将此 `Database` 元素与其根父为 `Server` 元素的元素（出现在 XML 输入文件的顶部）混淆。</span><span class="sxs-lookup"><span data-stu-id="66a3f-125">Do not confuse this `Database` element with the one whose root parent is the `Server` element, which occurs at the top of the XML input file.</span></span> <span data-ttu-id="66a3f-126">有关详细信息，请参阅[服务器的数据库元素 (DTA)](database-element-for-server-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="66a3f-126">For more information, see [Database Element for Server &#40;DTA&#41;](database-element-for-server-dta.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="66a3f-127">示例</span><span class="sxs-lookup"><span data-stu-id="66a3f-127">Example</span></span>  
 <span data-ttu-id="66a3f-128">有关此元素的用法示例 `Database` ，请参阅[使用用户指定的配置 &#40;DTA&#41;的 XML 输入文件示例](xml-input-file-sample-with-user-specified-configuration-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="66a3f-128">For a usage example of this `Database` element, see the [XML Input File Sample with User-specified Configuration &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66a3f-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="66a3f-129">See Also</span></span>  
 [<span data-ttu-id="66a3f-130">XML 输入文件引用（数据库引擎优化顾问）</span><span class="sxs-lookup"><span data-stu-id="66a3f-130">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
