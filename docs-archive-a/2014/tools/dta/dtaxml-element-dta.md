---
title: " (DTA) 的 DTAXML 元素 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- DTAXML element
ms.assetid: 3d9942ed-8a27-40db-a7c9-808984d914a2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9f428cf996bb819ece74c13226fcd5116a19142b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690975"
---
# <a name="dtaxml-element-dta"></a><span data-ttu-id="8d9ae-102">DTAXML 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="8d9ae-102">DTAXML Element (DTA)</span></span>
  <span data-ttu-id="8d9ae-103">数据库引擎优化顾问 XML 输入文件或输出文件的根元素 **DTAXML** 包含用于对数据库引擎优化顾问生成的优化输入和优化输出进行说明的所有元素。</span><span class="sxs-lookup"><span data-stu-id="8d9ae-103">The root element of a Database Engine Tuning Advisor XML input or output file, **DTAXML** contains all elements that describe tuning input and the tuning output that Database Engine Tuning Advisor generates.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d9ae-104">语法</span><span class="sxs-lookup"><span data-stu-id="8d9ae-104">Syntax</span></span>  
  
```  
  
<DTAXML   
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"   
    xmlns="https://schemas.microsoft.com/sqlserver/2004/07/dta">  
    ...code removed here...  
</DTAXML>  
```  
  
## <a name="element-attributes"></a><span data-ttu-id="8d9ae-105">元素属性</span><span class="sxs-lookup"><span data-stu-id="8d9ae-105">Element Attributes</span></span>  
  
|<span data-ttu-id="8d9ae-106">Attribute</span><span class="sxs-lookup"><span data-stu-id="8d9ae-106">Attribute</span></span>|<span data-ttu-id="8d9ae-107">说明</span><span class="sxs-lookup"><span data-stu-id="8d9ae-107">Description</span></span>|  
|---------------|-----------------|  
|`xmlns:xsi`|<span data-ttu-id="8d9ae-108">必需。</span><span class="sxs-lookup"><span data-stu-id="8d9ae-108">Required.</span></span> <span data-ttu-id="8d9ae-109">标识 XML 架构实例命名空间。</span><span class="sxs-lookup"><span data-stu-id="8d9ae-109">Identifies the XML Schema Instance namespace.</span></span> <span data-ttu-id="8d9ae-110">可以使用此命名空间中的属性来引用用于验证数据库引擎优化顾问 XML 文件的架构。</span><span class="sxs-lookup"><span data-stu-id="8d9ae-110">Attributes from this namespace are used to reference the schema that is used to validate the Database Engine Tuning Advisor XML file.</span></span><br /><br /> <span data-ttu-id="8d9ae-111">必需的值：[http://www.w3.org/2001/XMLSchema-instance](http://www.w3.org/2001/XMLSchema-instance)</span><span class="sxs-lookup"><span data-stu-id="8d9ae-111">Required value: [http://www.w3.org/2001/XMLSchema-instance](http://www.w3.org/2001/XMLSchema-instance)</span></span>|  
|`xmlns`|<span data-ttu-id="8d9ae-112">必需。</span><span class="sxs-lookup"><span data-stu-id="8d9ae-112">Required.</span></span> <span data-ttu-id="8d9ae-113">标识数据库引擎优化顾问命名空间。</span><span class="sxs-lookup"><span data-stu-id="8d9ae-113">Identifies the Database Engine Tuning Advisor namespace.</span></span><br /><br /> <span data-ttu-id="8d9ae-114">如果在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中使用 XML 编辑器编辑数据库引擎优化顾问 XML 文件，则“F1 帮助”和“动态帮助”将使用此值在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中定位可能的引用主题。</span><span class="sxs-lookup"><span data-stu-id="8d9ae-114">If you edit the Database Engine Tuning Advisor XML file using the XML editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], this value is used by F1 Help and Dynamic Help to locate possible reference topics in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span><br /><br /> <span data-ttu-id="8d9ae-115">必需的值：</span><span class="sxs-lookup"><span data-stu-id="8d9ae-115">Required value:</span></span><br /><br /> <span data-ttu-id="8d9ae-116">[Database Engine Tuning Advisor XML Schema](https://go.microsoft.com/fwlink/?LinkId=43100) （数据库引擎优化顾问 XML 架构）命名空间</span><span class="sxs-lookup"><span data-stu-id="8d9ae-116">[Database Engine Tuning Advisor XML Schema](https://go.microsoft.com/fwlink/?LinkId=43100) Namespace</span></span>|  
  
## <a name="element-characteristics"></a><span data-ttu-id="8d9ae-117">元素特征</span><span class="sxs-lookup"><span data-stu-id="8d9ae-117">Element Characteristics</span></span>  
  
|<span data-ttu-id="8d9ae-118">特征</span><span class="sxs-lookup"><span data-stu-id="8d9ae-118">Characteristic</span></span>|<span data-ttu-id="8d9ae-119">说明</span><span class="sxs-lookup"><span data-stu-id="8d9ae-119">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="8d9ae-120">**数据类型和长度**</span><span class="sxs-lookup"><span data-stu-id="8d9ae-120">**Data type and length**</span></span>|<span data-ttu-id="8d9ae-121">无。</span><span class="sxs-lookup"><span data-stu-id="8d9ae-121">None.</span></span>|  
|<span data-ttu-id="8d9ae-122">**默认值**</span><span class="sxs-lookup"><span data-stu-id="8d9ae-122">**Default value**</span></span>|<span data-ttu-id="8d9ae-123">无。</span><span class="sxs-lookup"><span data-stu-id="8d9ae-123">None.</span></span>|  
|<span data-ttu-id="8d9ae-124">**出现次数**</span><span class="sxs-lookup"><span data-stu-id="8d9ae-124">**Occurrence**</span></span>|<span data-ttu-id="8d9ae-125">每个 DTA XML 文件必须出现一次。</span><span class="sxs-lookup"><span data-stu-id="8d9ae-125">Required once per DTA XML file.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="8d9ae-126">元素关系</span><span class="sxs-lookup"><span data-stu-id="8d9ae-126">Element Relationships</span></span>  
  
|<span data-ttu-id="8d9ae-127">关系</span><span class="sxs-lookup"><span data-stu-id="8d9ae-127">Relationship</span></span>|<span data-ttu-id="8d9ae-128">元素</span><span class="sxs-lookup"><span data-stu-id="8d9ae-128">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="8d9ae-129">**父元素**</span><span class="sxs-lookup"><span data-stu-id="8d9ae-129">**Parent element**</span></span>|<span data-ttu-id="8d9ae-130">无</span><span class="sxs-lookup"><span data-stu-id="8d9ae-130">None</span></span>|  
|<span data-ttu-id="8d9ae-131">**子元素**</span><span class="sxs-lookup"><span data-stu-id="8d9ae-131">**Child elements**</span></span>|[<span data-ttu-id="8d9ae-132">DTAInput 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="8d9ae-132">DTAInput Element &#40;DTA&#41;</span></span>](dtainput-element-dta.md)<br /><br /> <span data-ttu-id="8d9ae-133">`DTAOutput`元素 (参阅[数据库引擎优化顾问 XML 架构](https://schemas.microsoft.com/sqlserver/)) </span><span class="sxs-lookup"><span data-stu-id="8d9ae-133">`DTAOutput` Element (see [Database Engine Tuning Advisor XML schema](https://schemas.microsoft.com/sqlserver/) for information)</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d9ae-134">备注</span><span class="sxs-lookup"><span data-stu-id="8d9ae-134">Remarks</span></span>  
 <span data-ttu-id="8d9ae-135">有关 XML namespaces 的详细信息，请参阅 [MSDN Library 中的](https://go.microsoft.com/fwlink/?LinkId=7341) Namespaces in an XML Document [!INCLUDE[msCoName](../../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="8d9ae-135">For more information about XML namespaces, see [Namespaces in an XML Document](https://go.microsoft.com/fwlink/?LinkId=7341) in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN Library.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d9ae-136">示例</span><span class="sxs-lookup"><span data-stu-id="8d9ae-136">Example</span></span>  
 <span data-ttu-id="8d9ae-137">有关典型 **DTAXML** 元素的示例，请参阅 [XML 输入文件实例 (DTA)](xml-input-file-samples-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="8d9ae-137">For examples of typical **DTAXML** elements, see [XML Input File Samples &#40;DTA&#41;](xml-input-file-samples-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d9ae-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8d9ae-138">See Also</span></span>  
 <span data-ttu-id="8d9ae-139">[XML 输入文件引用（数据库引擎优化顾问）](xml-input-file-reference-database-engine-tuning-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="8d9ae-139">[XML Input File Reference &#40;Database Engine Tuning Advisor&#41;](xml-input-file-reference-database-engine-tuning-advisor.md) </span></span>  
 [<span data-ttu-id="8d9ae-140">启动并使用数据库引擎优化顾问</span><span class="sxs-lookup"><span data-stu-id="8d9ae-140">Start and Use the Database Engine Tuning Advisor</span></span>](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md)  
  
  
