---
title: Server 元素 (DTA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Server element
ms.assetid: 9fe0bfb4-3aa6-4eb2-a83e-c0d0e7d4e9f6
author: stevestein
ms.author: sstein
ms.openlocfilehash: ab67e0303c2b629c3774886441474f5ef5b10a43
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588792"
---
# <a name="server-element-dta"></a><span data-ttu-id="32516-102">服务器元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="32516-102">Server Element (DTA)</span></span>
  <span data-ttu-id="32516-103">包含要优化的数据库所驻留的服务器的标识信息。</span><span class="sxs-lookup"><span data-stu-id="32516-103">Contains the identifying information for the server on which the databases reside that you want to tune.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32516-104">语法</span><span class="sxs-lookup"><span data-stu-id="32516-104">Syntax</span></span>  
  
```  
  
<DTAInput>  
    <Server>  
    ...code removed here...  
    </Server>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="32516-105">元素特征</span><span class="sxs-lookup"><span data-stu-id="32516-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="32516-106">特征</span><span class="sxs-lookup"><span data-stu-id="32516-106">Characteristic</span></span>|<span data-ttu-id="32516-107">说明</span><span class="sxs-lookup"><span data-stu-id="32516-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="32516-108">**数据类型和长度**</span><span class="sxs-lookup"><span data-stu-id="32516-108">**Data type and length**</span></span>|<span data-ttu-id="32516-109">无。</span><span class="sxs-lookup"><span data-stu-id="32516-109">None.</span></span>|  
|<span data-ttu-id="32516-110">**默认值**</span><span class="sxs-lookup"><span data-stu-id="32516-110">**Default value**</span></span>|<span data-ttu-id="32516-111">无。</span><span class="sxs-lookup"><span data-stu-id="32516-111">None.</span></span>|  
|<span data-ttu-id="32516-112">**出现次数**</span><span class="sxs-lookup"><span data-stu-id="32516-112">**Occurrence**</span></span>|<span data-ttu-id="32516-113">每个 `DTAInput` 元素必须出现一次。</span><span class="sxs-lookup"><span data-stu-id="32516-113">Required once per `DTAInput` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="32516-114">元素关系</span><span class="sxs-lookup"><span data-stu-id="32516-114">Element Relationships</span></span>  
  
|<span data-ttu-id="32516-115">关系</span><span class="sxs-lookup"><span data-stu-id="32516-115">Relationship</span></span>|<span data-ttu-id="32516-116">元素</span><span class="sxs-lookup"><span data-stu-id="32516-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="32516-117">**父元素**</span><span class="sxs-lookup"><span data-stu-id="32516-117">**Parent element**</span></span>|[<span data-ttu-id="32516-118">DTAInput 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="32516-118">DTAInput Element &#40;DTA&#41;</span></span>](dtainput-element-dta.md)|  
|<span data-ttu-id="32516-119">**子元素**</span><span class="sxs-lookup"><span data-stu-id="32516-119">**Child elements**</span></span>|[<span data-ttu-id="32516-120">服务器的名称元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="32516-120">Name Element for Server &#40;DTA&#41;</span></span>](name-element-for-server-dta.md)<br /><br /> [<span data-ttu-id="32516-121">服务器的数据库元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="32516-121">Database Element for Server &#40;DTA&#41;</span></span>](database-element-for-server-dta.md)|  
  
## <a name="remarks"></a><span data-ttu-id="32516-122">备注</span><span class="sxs-lookup"><span data-stu-id="32516-122">Remarks</span></span>  
 <span data-ttu-id="32516-123">只能为元素指定一个 `Server` 元素 `DTAInput` 。</span><span class="sxs-lookup"><span data-stu-id="32516-123">You can specify only one `Server` element for the `DTAInput` element.</span></span> <span data-ttu-id="32516-124">在 DTA XML 架构中，该元素的名称为 **ServerDetailsTypecomplexType** 。</span><span class="sxs-lookup"><span data-stu-id="32516-124">This element is of the **ServerDetailsTypecomplexType** name in the DTA XML schema.</span></span> <span data-ttu-id="32516-125">请不要将此 `Server` 元素与 `Configuration` 元素的子元素混淆。</span><span class="sxs-lookup"><span data-stu-id="32516-125">Do not confuse this `Server` element with the one that is the child of the `Configuration` element.</span></span> <span data-ttu-id="32516-126">有关详细信息，请参阅[用于配置的服务器元素 (DTA)](server-element-for-configuration-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="32516-126">For more information, see [Server Element for Configuration &#40;DTA&#41;](server-element-for-configuration-dta.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="32516-127">示例</span><span class="sxs-lookup"><span data-stu-id="32516-127">Example</span></span>  
 <span data-ttu-id="32516-128">以下示例说明如何在 SERVER001 的 **AdventureWorks** 数据库中指定 **Sales.SalesPerson** 表：</span><span class="sxs-lookup"><span data-stu-id="32516-128">The following example shows how to specify the **Sales.SalesPerson** table in the **AdventureWorks** database on SERVER001:</span></span>  
  
```xml  
<Server>  
  <Name>SERVER001</Name>  
  <Database>  
    <Name>AdventureWorks</Name>  
    <Schema>  
      <Name>Sales</Name>  
      <Table>  
        <Name>SalesPerson</Name>  
      </Table>  
    </Schema>  
  </Database>  
</Server  
```  
  
## <a name="see-also"></a><span data-ttu-id="32516-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="32516-129">See Also</span></span>  
 [<span data-ttu-id="32516-130">XML 输入文件引用（数据库引擎优化顾问）</span><span class="sxs-lookup"><span data-stu-id="32516-130">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
