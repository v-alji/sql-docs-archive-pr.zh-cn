---
title: " (DTA) 的文件元素 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- File element
ms.assetid: 73dce835-9a80-4aef-8e0f-9dcf07dd5b80
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0eeb2bdcc9513ca6283447daca63c8bbc4fa1726
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691449"
---
# <a name="file-element-dta"></a><span data-ttu-id="dc781-102">文件元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="dc781-102">File Element (DTA)</span></span>
  <span data-ttu-id="dc781-103">指定工作负荷文件。</span><span class="sxs-lookup"><span data-stu-id="dc781-103">Specifies the workload file.</span></span> <span data-ttu-id="dc781-104">工作负荷是对要优化的一个或多个数据库执行的一组 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="dc781-104">A workload is a set of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that execute against a database or databases that you want to tune.</span></span> <span data-ttu-id="dc781-105">工作负荷文件可以是 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本文件 (.sql)，也可以是跟踪文件 (.trc)。</span><span class="sxs-lookup"><span data-stu-id="dc781-105">Workload files can be [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts (.sql) or trace files (.trc).</span></span> <span data-ttu-id="dc781-106">有关详细信息，请参阅 [启动并使用数据库引擎优化顾问](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md)。</span><span class="sxs-lookup"><span data-stu-id="dc781-106">For more information, see [Start and Use the Database Engine Tuning Advisor](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc781-107">语法</span><span class="sxs-lookup"><span data-stu-id="dc781-107">Syntax</span></span>  
  
```  
  
<DTAInput>  
  <Server>...</Server>  
  <Workload>  
    <File>...</File>  
  </Workload>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="dc781-108">元素特征</span><span class="sxs-lookup"><span data-stu-id="dc781-108">Element Characteristics</span></span>  
  
|<span data-ttu-id="dc781-109">特征</span><span class="sxs-lookup"><span data-stu-id="dc781-109">Characteristic</span></span>|<span data-ttu-id="dc781-110">说明</span><span class="sxs-lookup"><span data-stu-id="dc781-110">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="dc781-111">**数据类型和长度**</span><span class="sxs-lookup"><span data-stu-id="dc781-111">**Data type and length**</span></span>|<span data-ttu-id="dc781-112">使用 `string` 数据类型，以指定工作负荷文件的目录路径。</span><span class="sxs-lookup"><span data-stu-id="dc781-112">Use the `string` data type to specify the directory path to your workload file.</span></span> <span data-ttu-id="dc781-113">例如：</span><span class="sxs-lookup"><span data-stu-id="dc781-113">For example:</span></span><br /><br /> `<File>C:\Tuning\tun.sql</File>`<br /><br /> <span data-ttu-id="dc781-114">长度限制由服务器强制执行。</span><span class="sxs-lookup"><span data-stu-id="dc781-114">Length limit is enforced by the server.</span></span>|  
|<span data-ttu-id="dc781-115">**默认值**</span><span class="sxs-lookup"><span data-stu-id="dc781-115">**Default value**</span></span>|<span data-ttu-id="dc781-116">无。</span><span class="sxs-lookup"><span data-stu-id="dc781-116">None.</span></span>|  
|<span data-ttu-id="dc781-117">**出现次数**</span><span class="sxs-lookup"><span data-stu-id="dc781-117">**Occurrence**</span></span>|<span data-ttu-id="dc781-118">如果未指定其他类型的工作负荷，则必须使用一次。</span><span class="sxs-lookup"><span data-stu-id="dc781-118">Required once if no other type of workload is specified.</span></span> <span data-ttu-id="dc781-119">必须为父元素 **EventString**指定子元素 **File**、 **Database** 或 **Workload** ，但只能使用一种类型。</span><span class="sxs-lookup"><span data-stu-id="dc781-119">You must specify an **EventString**, a **File**, or a **Database** child element for the **Workload** parent, but only one type can be used.</span></span> <span data-ttu-id="dc781-120">例如，如果用 **文件** 元素指定工作负荷，则不能在同一 XML 输入文件中又用 **数据库** 元素指定工作负荷。</span><span class="sxs-lookup"><span data-stu-id="dc781-120">For example, if you specify a workload with the **File** element, then you cannot also specify a workload with the **Database** element in the same XML input file.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="dc781-121">元素关系</span><span class="sxs-lookup"><span data-stu-id="dc781-121">Element Relationships</span></span>  
  
|<span data-ttu-id="dc781-122">关系</span><span class="sxs-lookup"><span data-stu-id="dc781-122">Relationship</span></span>|<span data-ttu-id="dc781-123">元素</span><span class="sxs-lookup"><span data-stu-id="dc781-123">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="dc781-124">**父元素**</span><span class="sxs-lookup"><span data-stu-id="dc781-124">**Parent element**</span></span>|[<span data-ttu-id="dc781-125">工作负荷元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="dc781-125">Workload Element &#40;DTA&#41;</span></span>](workload-element-dta.md)|  
|<span data-ttu-id="dc781-126">**子元素**</span><span class="sxs-lookup"><span data-stu-id="dc781-126">**Child elements**</span></span>|<span data-ttu-id="dc781-127">无。</span><span class="sxs-lookup"><span data-stu-id="dc781-127">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="dc781-128">示例</span><span class="sxs-lookup"><span data-stu-id="dc781-128">Example</span></span>  
 <span data-ttu-id="dc781-129">有关该元素的使用示例，请参阅[简单 XML 输入文件示例 (DTA)](simple-xml-input-file-sample-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="dc781-129">For a usage example of this element, see [Simple XML Input File Sample &#40;DTA&#41;](simple-xml-input-file-sample-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc781-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dc781-130">See Also</span></span>  
 [<span data-ttu-id="dc781-131">XML 输入文件引用（数据库引擎优化顾问）</span><span class="sxs-lookup"><span data-stu-id="dc781-131">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
