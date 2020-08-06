---
title: 工作负荷的数据库元素 (DTA) | Microsoft Docs
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
ms.assetid: 112fca2a-37e5-4162-b2e7-b56eb8ab0c6f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2774bc7ed981c84c966a394c95347208cbc6d656
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682538"
---
# <a name="database-element-for-workload-dta"></a><span data-ttu-id="f0321-102">工作负荷的数据库元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="f0321-102">Database Element for Workload (DTA)</span></span>
  <span data-ttu-id="f0321-103">指定工作负荷跟踪表所在的数据库。</span><span class="sxs-lookup"><span data-stu-id="f0321-103">Specifies the database where the workload trace table is located.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0321-104">语法</span><span class="sxs-lookup"><span data-stu-id="f0321-104">Syntax</span></span>  
  
```  
  
<Workload>  
  <Database>  
   ...code removed here...  
  </Database>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="f0321-105">元素特征</span><span class="sxs-lookup"><span data-stu-id="f0321-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="f0321-106">特征</span><span class="sxs-lookup"><span data-stu-id="f0321-106">Characteristic</span></span>|<span data-ttu-id="f0321-107">说明</span><span class="sxs-lookup"><span data-stu-id="f0321-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="f0321-108">**数据类型和长度**</span><span class="sxs-lookup"><span data-stu-id="f0321-108">**Data type and length**</span></span>|<span data-ttu-id="f0321-109">无。</span><span class="sxs-lookup"><span data-stu-id="f0321-109">None.</span></span>|  
|<span data-ttu-id="f0321-110">**默认值**</span><span class="sxs-lookup"><span data-stu-id="f0321-110">**Default value**</span></span>|<span data-ttu-id="f0321-111">无。</span><span class="sxs-lookup"><span data-stu-id="f0321-111">None.</span></span>|  
|<span data-ttu-id="f0321-112">**出现次数**</span><span class="sxs-lookup"><span data-stu-id="f0321-112">**Occurrence**</span></span>|<span data-ttu-id="f0321-113">如果未指定其他类型的工作负荷，则必须使用一次。</span><span class="sxs-lookup"><span data-stu-id="f0321-113">Required once if no other type of workload is specified.</span></span> <span data-ttu-id="f0321-114">必须为父元素 `EventString` 指定子元素 `File`、`Database` 或 `Workload`，但只能使用一种类型。</span><span class="sxs-lookup"><span data-stu-id="f0321-114">You must specify an `EventString`, a `File`, or a `Database` child element for the `Workload` parent, but only one type can be used.</span></span> <span data-ttu-id="f0321-115">例如，如果使用 `Database` 元素指定了工作负荷，则不可以在同一 XML 输入文件中使用 `File` 元素指定工作负荷。</span><span class="sxs-lookup"><span data-stu-id="f0321-115">For example, if you specify a workload with the `Database` element, you cannot also specify a workload with the `File` element in the same XML input file.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="f0321-116">元素关系</span><span class="sxs-lookup"><span data-stu-id="f0321-116">Element Relationships</span></span>  
  
|<span data-ttu-id="f0321-117">关系</span><span class="sxs-lookup"><span data-stu-id="f0321-117">Relationship</span></span>|<span data-ttu-id="f0321-118">元素</span><span class="sxs-lookup"><span data-stu-id="f0321-118">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="f0321-119">**父元素**</span><span class="sxs-lookup"><span data-stu-id="f0321-119">**Parent element**</span></span>|[<span data-ttu-id="f0321-120">工作负荷元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="f0321-120">Workload Element &#40;DTA&#41;</span></span>](workload-element-dta.md)|  
|<span data-ttu-id="f0321-121">**子元素**</span><span class="sxs-lookup"><span data-stu-id="f0321-121">**Child elements**</span></span>|[<span data-ttu-id="f0321-122">数据库的名称元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="f0321-122">Name Element for Database &#40;DTA&#41;</span></span>](name-element-for-database-dta.md)<br /><br /> [<span data-ttu-id="f0321-123">数据库的架构元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="f0321-123">Schema Element for Database &#40;DTA&#41;</span></span>](schema-element-for-database-dta.md)|  
  
## <a name="remarks"></a><span data-ttu-id="f0321-124">备注</span><span class="sxs-lookup"><span data-stu-id="f0321-124">Remarks</span></span>  
 <span data-ttu-id="f0321-125">在数据库引擎优化顾问 XML 架构中，此元素的名称为 **DatabaseDetailsTypecomplexType** 。</span><span class="sxs-lookup"><span data-stu-id="f0321-125">This element is of the **DatabaseDetailsTypecomplexType** name in the Database Engine Tuning Advisor XML schema.</span></span> <span data-ttu-id="f0321-126">请不要将此 `Database` 元素与根级父元素为 `Configuration` 元素的元素相混淆。</span><span class="sxs-lookup"><span data-stu-id="f0321-126">Do not confuse this `Database` element with the one whose root parent is the `Configuration` element.</span></span> <span data-ttu-id="f0321-127">（请参阅[用于配置的数据库元素 (DTA)](database-element-for-configuration-dta.md)。）</span><span class="sxs-lookup"><span data-stu-id="f0321-127">(See [Database Element for Configuration &#40;DTA&#41;](database-element-for-configuration-dta.md).)</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0321-128">示例</span><span class="sxs-lookup"><span data-stu-id="f0321-128">Example</span></span>  
 <span data-ttu-id="f0321-129">有关此元素的用法示例 `Database` ，请参阅[工作负荷元素](workload-element-dta.md)中的代码示例 &#40;DTA&#41;。</span><span class="sxs-lookup"><span data-stu-id="f0321-129">For a usage example of this `Database` element, see the code example in [Workload Element &#40;DTA&#41;](workload-element-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0321-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f0321-130">See Also</span></span>  
 [<span data-ttu-id="f0321-131">XML 输入文件引用（数据库引擎优化顾问）</span><span class="sxs-lookup"><span data-stu-id="f0321-131">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
